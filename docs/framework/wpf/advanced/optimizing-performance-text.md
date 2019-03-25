---
title: 'Otimizando desempenho: Texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
ms.openlocfilehash: 14751d8241dabd0cf7c41f2920fab32e21dc43e2
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409400"
---
# <a name="optimizing-performance-text"></a>Otimizando desempenho: Texto
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui suporte para a apresentação do conteúdo de texto com o uso de controles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] com recursos sofisticados. Em geral, você pode dividir a renderização de texto em três camadas:  
  
1.  Usando o <xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun> objetos diretamente.  
  
2.  Usando o <xref:System.Windows.Media.FormattedText> objeto.  
  
3.  Usando controles de alto nível, como o <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument> objetos.  
  
 Este tópico apresenta recomendações de desempenho de renderização de texto.  
  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Renderização de texto no nível de glifos  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suporte avançado de texto incluindo marcação em nível de glifos com acesso direto ao <xref:System.Windows.Documents.Glyphs> para clientes que desejam interceptar e persistir texto após a formatação. Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.  
  
-   Exibição em tela de documentos de formato fixo.  
  
-   Cenários de impressão.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como uma linguagem de impressora do dispositivo.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   A saída de drivers de impressão anteriores é de aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] para o formato fixo.  
  
    -   Formato do spool de impressão.  
  
-   Representação de documentos de formato fixo, incluindo clientes de versões anteriores do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e outros dispositivos de computação.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun> são projetados para apresentação de documentos de formato fixo e cenários de impressão. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece vários elementos para layout geral e [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] cenários, como <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.TextBlock>. Para mais informações sobre layout e cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Tipografia no WPF](typography-in-wpf.md).  
  
 Os exemplos a seguir mostram como definir propriedades para um <xref:System.Windows.Documents.Glyphs> do objeto no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. O <xref:System.Windows.Documents.Glyphs> objeto representa a saída de um <xref:System.Windows.Media.GlyphRun> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Os exemplos assumem que as fontes Arial, Courier New e Times New Roman estão instaladas na pasta **C:\WINDOWS\Fontes** no computador local.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>Usando DrawGlyphRun  
 Se você tiver controle personalizado e desejar renderizar glifos, use o <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> método.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também fornece serviços de nível inferior para formatação através do uso de texto personalizado a <xref:System.Windows.Media.FormattedText> objeto. A maneira mais eficiente de renderizar texto em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é gerar conteúdo de texto no nível de glifo usando <xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun>. No entanto, o custo dessa eficiência é a perda de fácil de usar formatação rich text, que são recursos internos de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] controles, como <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>Objeto FormattedText  
 O <xref:System.Windows.Media.FormattedText> objeto permite que você desenhe texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. Para mais informações, consulte [Desenhando texto formatado](drawing-formatted-text.md).  
  
 Para criar texto formatado, chame o <xref:System.Windows.Media.FormattedText.%23ctor%2A> construtor para criar um <xref:System.Windows.Media.FormattedText> objeto. Após ter criado a cadeia de caracteres de texto formatado inicial, você poderá aplicar uma variedade de estilos de formatação. Se seu aplicativo deseja implementar seu próprio layout, em seguida, a <xref:System.Windows.Media.FormattedText> objeto é uma opção melhor que o uso de um controle, tal como <xref:System.Windows.Controls.TextBlock>. Para obter mais informações sobre o <xref:System.Windows.Media.FormattedText> do objeto, consulte [Desenhando texto formatado](drawing-formatted-text.md) .  
  
 O <xref:System.Windows.Media.FormattedText> objeto fornece funcionalidades de formatação de texto de nível baixo. É possível aplicar vários estilos de formatação a um ou mais caracteres. Por exemplo, você poderia chamar ambos os <xref:System.Windows.Media.FormattedText.SetFontSize%2A> e <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> métodos para alterar a formatação dos cinco primeiros caracteres no texto.  
  
 O exemplo de código a seguir cria um <xref:System.Windows.Media.FormattedText> do objeto e renderiza-o.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>Controles de rótulo, TextBlock e FlowDocument  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>O FlowDocument impacta o desempenho mais do que o TextBlock ou o Rótulo  
 Em geral, o <xref:System.Windows.Controls.TextBlock> elemento deve ser usado quando suporte limitado a texto é necessário, como uma breve frase em um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> pode ser usado quando suporte mínimo a texto é necessário. O <xref:System.Windows.Documents.FlowDocument> elemento é um contêiner para documentos re-flowable que dão suporte à apresentação avançada de conteúdo e, portanto, tem um impacto de desempenho maior do que usando o <xref:System.Windows.Controls.TextBlock> ou <xref:System.Windows.Controls.Label> controles.  
  
 Para obter mais informações sobre <xref:System.Windows.Documents.FlowDocument>, consulte [visão geral do documento de fluxo](flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>Evite usar TextBlock em FlowDocument  
 O <xref:System.Windows.Controls.TextBlock> elemento é derivado de <xref:System.Windows.UIElement>. O <xref:System.Windows.Documents.Run> elemento é derivado de <xref:System.Windows.Documents.TextElement>, que é menos dispendioso de usar do que um <xref:System.Windows.UIElement>-objeto derivado. Quando possível, use <xref:System.Windows.Documents.Run> em vez de <xref:System.Windows.Controls.TextBlock> para exibir o conteúdo de texto em um <xref:System.Windows.Documents.FlowDocument>.  
  
 O exemplo de marcação a seguir ilustra duas maneiras de definir o conteúdo de texto em um <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Evite usar Run para definir propriedades de texto  
 Em geral, usando um <xref:System.Windows.Documents.Run> dentro de um <xref:System.Windows.Controls.TextBlock> é o desempenho mais intensa que o não uso explícito <xref:System.Windows.Documents.Run> do objeto em todos os. Se você estiver usando um <xref:System.Windows.Documents.Run> para definir propriedades de texto, defina essas propriedades diretamente no <xref:System.Windows.Controls.TextBlock> em vez disso.  
  
 O exemplo de marcação a seguir ilustra essas duas maneiras de definir uma propriedade de texto, nesse caso, o <xref:System.Windows.Controls.TextBlock.FontWeight%2A> propriedade:  
  
 [!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 A tabela a seguir mostra o custo de exibir 1000 <xref:System.Windows.Controls.TextBlock> objetos com e sem um explícito <xref:System.Windows.Documents.Run>.  
  
|**Tipo TextBlock**|**Tempo de criação (ms)**|**Tempo de renderização (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Propriedades de texto de configuração Run|146|540|  
|Propriedades de texto de configuração TextBlock|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Evite a associação de dados com a propriedade Label.Content  
 Imagine um cenário em que você tenha um <xref:System.Windows.Controls.Label> objeto que é atualizado com frequência de um <xref:System.String> código-fonte. Quando a associação de dados a <xref:System.Windows.Controls.Label> do elemento <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade para o <xref:System.String> objeto de origem, você pode enfrentar um desempenho ruim. Cada vez que o código-fonte <xref:System.String> é atualizado, o antigo <xref:System.String> objeto é descartado e um novo <xref:System.String> é recriado — porque um <xref:System.String> objeto é imutável, ele não pode ser modificado. Isso, por sua vez, faz o <xref:System.Windows.Controls.ContentPresenter> do <xref:System.Windows.Controls.Label> objeto descarte seu conteúdo antigo e gere novamente o novo conteúdo para exibir a nova <xref:System.String>.  
  
 A solução para esse problema é simples. Se o <xref:System.Windows.Controls.Label> não está definido como personalizado <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> valor, substitua o <xref:System.Windows.Controls.Label> com um <xref:System.Windows.Controls.TextBlock> e associar dados seu <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade na cadeia de caracteres de origem.  
  
|**Propriedade associada de dados**|**Tempo de atualização (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Hiperlink  
 O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de fluxo de nível embutido que permite hospedar hiperlinks dentro do conteúdo de fluxo.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Combinando hiperlinks em um objeto TextBlock  
 Você pode otimizar o uso de várias <xref:System.Windows.Documents.Hyperlink> elementos, agrupando-os juntos no mesmo <xref:System.Windows.Controls.TextBlock>. Isso ajuda a minimizar o número de objetos criados em seu aplicativo. Por exemplo, você talvez queira exibir vários hiperlinks, como o seguinte:  
  
 Página inicial do MSN &#124; Meu MSN  
  
 O exemplo de marcação a seguir mostra vários <xref:System.Windows.Controls.TextBlock> elementos usados para exibir os hiperlinks:  
  
 [!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 O exemplo de marcação a seguir mostra uma maneira mais eficiente de exibir os hiperlinks, desta vez, usando um único <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Mostrando sublinhados em hiperlinks somente em eventos MouseEnter  
 Um <xref:System.Windows.TextDecoration> objeto é um Ornamento visual que você pode adicionar ao texto; no entanto, ele pode ser desempenho intenso para instanciar. Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, considere mostrar um sublinhado somente ao disparar um evento, como o <xref:System.Windows.ContentElement.MouseEnter> eventos. Para obter mais informações, consulte [Especificar se um hiperlink está sublinhado](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
  A imagem a seguir mostra como o evento MouseEnter dispara o hiperlink sublinhado:

  ![Hiperlinks exibindo TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)   
  
 O exemplo de marcação a seguir mostra um <xref:System.Windows.Documents.Hyperlink> definido com e sem sublinhado:  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 A tabela a seguir mostra o custo de desempenho de exibir 1000 <xref:System.Windows.Documents.Hyperlink> elementos com e sem sublinhado.  
  
|**Hiperlink**|**Tempo de criação (ms)**|**Tempo de renderização (ms)**|  
|-------------------|------------------------------|----------------------------|  
|Com sublinhado|289|1130|  
|Sem sublinhado|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Recursos de formatação de texto  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece serviços de formatação de texto avançado, como hifenizações automáticas. Esses serviços podem afetar o desempenho do aplicativo e devem ser usados somente quando necessário.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Evite o uso desnecessário de hifenização  
 A hifenização automática localiza pontos de interrupção de hífen para linhas de texto e permite posições adicionais de quebra de linhas no <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument> objetos. Por padrão, o recurso de hifenização automática está desabilitado nesses objetos. Você pode habilitar esse recurso configurando a propriedade IsHyphenationEnabled do objeto como `true`. No entanto, habilitar esse recurso faz com que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inicie a interoperabilidade [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], que pode afetar o desempenho do aplicativo. É recomendável que você não use a hifenização automática, a menos que necessário.  
  
### <a name="use-figures-carefully"></a>Use as figuras com cuidado  
 Um <xref:System.Windows.Documents.Figure> elemento representa uma parte do conteúdo de fluxo que pode ser posicionada absolutamente dentro de uma página de conteúdo. Em alguns casos, um <xref:System.Windows.Documents.Figure> pode fazer com que uma página inteira seja reformatada automaticamente se a sua posição colidir com conteúdo que já foi posicionado. Você pode minimizar a possibilidade de reformatação desnecessária agrupamento <xref:System.Windows.Documents.Figure> elementos uns aos outros ou declará-los na parte superior do conteúdo em um cenário de tamanho fixo de página.  
  
### <a name="optimal-paragraph"></a>Parágrafo ideal  
 O recurso de parágrafo ideal o <xref:System.Windows.Documents.FlowDocument> objeto dispõe parágrafos para que o espaço em branco seja distribuído de maneira mais uniforme possível. Por padrão, o recurso de parágrafo otimizado é desabilitado. Você pode habilitar esse recurso, definindo o objeto <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> propriedade para `true`. No entanto, habilitar esse recurso afeta o desempenho do aplicativo. É recomendável que você não use o recurso de parágrafo ideal, a menos que necessário.  
  
## <a name="see-also"></a>Consulte também
- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
