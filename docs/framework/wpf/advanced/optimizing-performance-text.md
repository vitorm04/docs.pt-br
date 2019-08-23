---
title: 'Otimizando o desempenho: Texto'
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
ms.openlocfilehash: 318972c20f6461489226e19b3e517ba0ac069b28
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933359"
---
# <a name="optimizing-performance-text"></a>Otimizando o desempenho: Texto

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui suporte para a apresentação do conteúdo de texto com o uso de controles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] com recursos sofisticados. Em geral, você pode dividir a renderização de texto em três camadas:

1. Usando os <xref:System.Windows.Documents.Glyphs> objetos <xref:System.Windows.Media.GlyphRun> e diretamente.

2. Usando o <xref:System.Windows.Media.FormattedText> objeto.

3. Usando controles de alto nível, como os <xref:System.Windows.Controls.TextBlock> objetos e. <xref:System.Windows.Documents.FlowDocument>

Este tópico apresenta recomendações de desempenho de renderização de texto.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Renderização de texto no nível de glifos

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fornece suporte de texto avançado, incluindo marcação de nível de glifo com <xref:System.Windows.Documents.Glyphs> acesso direto ao para clientes que desejam interceptar e persistir texto após a formatação. Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.

- Exibição em tela de documentos de formato fixo.

- Cenários de impressão.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como uma linguagem de impressora do dispositivo.

  - Microsoft XPS Document Writer.

  - A saída de drivers de impressão anteriores é de aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] para o formato fixo.

  - Formato do spool de impressão.

- Representação de documento de formato fixo, incluindo clientes para versões anteriores do Windows e outros dispositivos de computação.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>e <xref:System.Windows.Media.GlyphRun> são projetados para cenários de impressão e apresentação de documentos de formato fixo. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fornece vários elementos para layout geral e [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] cenários <xref:System.Windows.Controls.Label> como e <xref:System.Windows.Controls.TextBlock>. Para mais informações sobre layout e cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Tipografia no WPF](typography-in-wpf.md).

Os exemplos a seguir mostram como definir propriedades para um <xref:System.Windows.Documents.Glyphs> objeto no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. O <xref:System.Windows.Documents.Glyphs> objeto representa a saída de um <xref:System.Windows.Media.GlyphRun> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Os exemplos assumem que as fontes Arial, Courier New e Times New Roman estão instaladas na pasta **C:\WINDOWS\Fontes** no computador local.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Usando DrawGlyphRun

Se você tiver um controle personalizado e quiser renderizar glifos, use o <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> método.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também fornece serviços de nível inferior para formatação de texto personalizado por meio do uso <xref:System.Windows.Media.FormattedText> do objeto. A maneira mais eficiente de renderizar texto [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] no é gerar o conteúdo de texto no nível de <xref:System.Windows.Documents.Glyphs> glifo <xref:System.Windows.Media.GlyphRun>usando e. No entanto, o custo dessa eficiência é a perda de formatação de Rich Text fácil de usar, que são recursos internos de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] controles, <xref:System.Windows.Controls.TextBlock> como e <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Objeto FormattedText

O <xref:System.Windows.Media.FormattedText> objeto permite desenhar texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. Para mais informações, consulte [Desenhando texto formatado](drawing-formatted-text.md).

Para criar texto formatado, chame o <xref:System.Windows.Media.FormattedText.%23ctor%2A> Construtor para criar um <xref:System.Windows.Media.FormattedText> objeto. Após ter criado a cadeia de caracteres de texto formatado inicial, você poderá aplicar uma variedade de estilos de formatação. Se o seu aplicativo quiser implementar seu próprio layout, o <xref:System.Windows.Media.FormattedText> objeto será melhor escolha do que usar um controle, <xref:System.Windows.Controls.TextBlock>como. Para obter mais informações sobre <xref:System.Windows.Media.FormattedText> o objeto, consulte [desenho de texto formatado](drawing-formatted-text.md) .

O <xref:System.Windows.Media.FormattedText> objeto fornece a capacidade de formatação de texto de baixo nível. É possível aplicar vários estilos de formatação a um ou mais caracteres. Por exemplo, você poderia chamar ambos os <xref:System.Windows.Media.FormattedText.SetFontSize%2A> métodos <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> e para alterar a formatação dos cinco primeiros caracteres no texto.

O exemplo de código a seguir <xref:System.Windows.Media.FormattedText> cria um objeto e o renderiza.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Controles de rótulo, TextBlock e FlowDocument

O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>O FlowDocument impacta o desempenho mais do que o TextBlock ou o Rótulo

Em geral, o <xref:System.Windows.Controls.TextBlock> elemento deve ser usado quando o suporte a texto limitado é necessário, como uma breve frase em [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]um. <xref:System.Windows.Controls.Label>pode ser usado quando o suporte a texto mínimo é necessário. O <xref:System.Windows.Documents.FlowDocument> elemento é um contêiner para documentos refluíáveis que dão suporte à apresentação avançada de conteúdo e, portanto, tem um impacto maior no desempenho do <xref:System.Windows.Controls.TextBlock> que <xref:System.Windows.Controls.Label> o uso dos controles ou.

Para obter mais informações <xref:System.Windows.Documents.FlowDocument>sobre o, consulte [visão geral do documento de fluxo](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Evite usar TextBlock em FlowDocument

O <xref:System.Windows.Controls.TextBlock> elemento é derivado de <xref:System.Windows.UIElement>. O <xref:System.Windows.Documents.Run> elemento é derivado de <xref:System.Windows.Documents.TextElement>, que é menos dispendioso para ser usado do <xref:System.Windows.UIElement>que um objeto derivado. Quando possível, use <xref:System.Windows.Documents.Run> em vez <xref:System.Windows.Controls.TextBlock> de exibir o conteúdo de texto <xref:System.Windows.Documents.FlowDocument>em um.

O exemplo de marcação a seguir ilustra duas maneiras de definir o conteúdo <xref:System.Windows.Documents.FlowDocument>de texto em um:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Evite usar Run para definir propriedades de texto

Em geral, usar um <xref:System.Windows.Documents.Run> dentro de <xref:System.Windows.Controls.TextBlock> um é mais intensivo em desempenho do que não <xref:System.Windows.Documents.Run> usar um objeto explícito. Se você estiver usando um <xref:System.Windows.Documents.Run> para definir propriedades de texto, defina essas propriedades diretamente <xref:System.Windows.Controls.TextBlock> no em vez disso.

O exemplo de marcação a seguir ilustra essas duas maneiras de definir uma propriedade de texto, nesse caso <xref:System.Windows.Controls.TextBlock.FontWeight%2A> , a propriedade:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

A tabela a seguir mostra o custo da exibição <xref:System.Windows.Controls.TextBlock> de 1000 objetos com e sem <xref:System.Windows.Documents.Run>um explícito.

|**Tipo TextBlock**|**Tempo de criação (ms)**|**Tempo de renderização (ms)**|
|------------------------|------------------------------|----------------------------|
|Propriedades de texto de configuração Run|146|540|
|Propriedades de texto de configuração TextBlock|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Evite a associação de dados com a propriedade Label.Content

Imagine um cenário em que você tenha <xref:System.Windows.Controls.Label> um objeto que é atualizado com frequência <xref:System.String> a partir de uma origem. Quando os dados são <xref:System.Windows.Controls.Label> vinculados <xref:System.Windows.Controls.ContentControl.Content%2A> à propriedade do <xref:System.String> elemento para o objeto de origem, você pode experimentar um desempenho insatisfatório. Cada vez que a <xref:System.String> origem é atualizada, o <xref:System.String> objeto antigo é Descartado e um novo <xref:System.String> é recriado — porque um <xref:System.String> objeto é imutável, ele não pode ser modificado. Isso, por sua vez, faz <xref:System.Windows.Controls.ContentPresenter> com que <xref:System.Windows.Controls.Label> o do objeto descarte seu conteúdo antigo e gere novamente o novo conteúdo para exibir o <xref:System.String>novo.

A solução para esse problema é simples. Se o <xref:System.Windows.Controls.Label> não estiver definido como um valor <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> personalizado <xref:System.Windows.Controls.TextBlock> , substitua o <xref:System.Windows.Controls.Label> por a e os dados vinculam sua <xref:System.Windows.Controls.TextBlock.Text%2A> Propriedade à cadeia de caracteres de origem.

|**Propriedade associada de dados**|**Tempo de atualização (ms)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Hiperlink

O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de fluxo de nível embutido que permite hospedar hiperlinks dentro do conteúdo do fluxo.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Combinando hiperlinks em um objeto TextBlock

Você pode otimizar o uso de vários <xref:System.Windows.Documents.Hyperlink> elementos agrupando-os juntos dentro do <xref:System.Windows.Controls.TextBlock>mesmo. Isso ajuda a minimizar o número de objetos criados em seu aplicativo. Por exemplo, você talvez queira exibir vários hiperlinks, como o seguinte:

Página inicial do MSN &#124; Meu MSN

O exemplo de marcação a seguir <xref:System.Windows.Controls.TextBlock> mostra vários elementos usados para exibir os hiperlinks:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

O exemplo de marcação a seguir mostra uma maneira mais eficiente de exibir os hiperlinks, desta vez, usando <xref:System.Windows.Controls.TextBlock>um único:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Mostrando sublinhados em hiperlinks somente em eventos MouseEnter

Um <xref:System.Windows.TextDecoration> objeto é uma ornamentação visual que você pode adicionar ao texto; no entanto, ele pode ser de uso intensivo de desempenho para instanciar. Se você fizer amplo uso de <xref:System.Windows.Documents.Hyperlink> elementos, considere mostrar um sublinhado somente ao disparar um evento, como o <xref:System.Windows.ContentElement.MouseEnter> evento. Para obter mais informações, consulte [Especificar se um hiperlink está sublinhado](how-to-specify-whether-a-hyperlink-is-underlined.md).

A imagem a seguir mostra como o evento MouseEnter dispara o hiperlink sublinhado:

![Hiperlinks exibindo TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

O exemplo de marcação a seguir <xref:System.Windows.Documents.Hyperlink> mostra um definido com e sem um sublinhado:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

A tabela a seguir mostra o custo de desempenho da <xref:System.Windows.Documents.Hyperlink> exibição de 1000 elementos com e sem um sublinhado.

|**Hiperlink**|**Tempo de criação (ms)**|**Tempo de renderização (ms)**|
|-------------------|------------------------------|----------------------------|
|Com sublinhado|289|1130|
|Sem sublinhado|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Recursos de formatação de texto

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece serviços de formatação de texto avançado, como hifenizações automáticas. Esses serviços podem afetar o desempenho do aplicativo e devem ser usados somente quando necessário.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Evite o uso desnecessário de hifenização

A hifenização automática localiza pontos de interrupção de hífen para linhas de texto e permite posições de quebra adicionais <xref:System.Windows.Controls.TextBlock> para <xref:System.Windows.Documents.FlowDocument> linhas em objetos e. Por padrão, o recurso de hifenização automática está desabilitado nesses objetos. Você pode habilitar esse recurso configurando a propriedade IsHyphenationEnabled do objeto como `true`. No entanto, a habilitação desse recurso faz com que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o inicie a interoperabilidade Component Object Model (com), o que pode afetar o desempenho do aplicativo. É recomendável que você não use a hifenização automática, a menos que necessário.

### <a name="use-figures-carefully"></a>Use as figuras com cuidado

Um <xref:System.Windows.Documents.Figure> elemento representa uma parte do conteúdo do fluxo que pode ser absolutamente posicionado em uma página de conteúdo. Em alguns casos, um <xref:System.Windows.Documents.Figure> pode fazer com que uma página inteira reformate automaticamente se sua posição colide com o conteúdo que já foi definido. Você pode minimizar a possibilidade de reformatação desnecessária agrupando <xref:System.Windows.Documents.Figure> elementos ao lado um do outro ou declarando-os próximo à parte superior do conteúdo em um cenário de tamanho de página fixo.

### <a name="optimal-paragraph"></a>Parágrafo ideal

O recurso de parágrafo ideal do <xref:System.Windows.Documents.FlowDocument> objeto apresenta parágrafos para que o espaço em branco seja distribuído da maneira mais uniforme possível. Por padrão, o recurso de parágrafo otimizado é desabilitado. Você pode habilitar esse recurso definindo a propriedade do <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> objeto como. `true` No entanto, habilitar esse recurso afeta o desempenho do aplicativo. É recomendável que você não use o recurso de parágrafo ideal, a menos que necessário.

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
