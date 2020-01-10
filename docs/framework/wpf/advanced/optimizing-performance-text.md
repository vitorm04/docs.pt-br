---
title: 'Otimizando desempenho: texto'
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
ms.openlocfilehash: 3e729458538353499f27f95ea2ca37fea1335238
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740346"
---
# <a name="optimizing-performance-text"></a>Otimizando desempenho: texto

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui suporte para a apresentação do conteúdo de texto com o uso de controles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] com recursos sofisticados. Em geral, você pode dividir a renderização de texto em três camadas:

1. Usando os objetos <xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun> diretamente.

2. Usando o objeto <xref:System.Windows.Media.FormattedText>.

3. Usando controles de alto nível, como os objetos <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument>.

Este tópico apresenta recomendações de desempenho de renderização de texto.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Renderização de texto no nível de glifos

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suporte de texto avançado, incluindo marcação de nível de glifo com acesso direto a <xref:System.Windows.Documents.Glyphs> para clientes que desejam interceptar e persistir texto após a formatação. Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.

- Exibição em tela de documentos de formato fixo.

- Cenários de impressão.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como uma linguagem de impressora do dispositivo.

  - Microsoft XPS Document Writer.

  - Drivers de impressora anteriores, saída de aplicativos Win32 para o formato fixo.

  - Formato do spool de impressão.

- Representação de documento de formato fixo, incluindo clientes para versões anteriores do Windows e outros dispositivos de computação.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun> são projetados para cenários de impressão e apresentação de documentos de formato fixo. o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece vários elementos para o layout geral e cenários de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], como <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.TextBlock>. Para mais informações sobre layout e cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Tipografia no WPF](typography-in-wpf.md).

Os exemplos a seguir mostram como definir propriedades para um objeto <xref:System.Windows.Documents.Glyphs> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. O objeto <xref:System.Windows.Documents.Glyphs> representa a saída de um <xref:System.Windows.Media.GlyphRun> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Os exemplos assumem que as fontes Arial, Courier New e Times New Roman estão instaladas na pasta **C:\WINDOWS\Fontes** no computador local.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Usando DrawGlyphRun

Se você tiver um controle personalizado e quiser renderizar glifos, use o método <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também fornece serviços de nível inferior para formatação de texto personalizado por meio do uso do objeto <xref:System.Windows.Media.FormattedText>. A maneira mais eficiente de renderizar texto em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é gerar o conteúdo de texto no nível de glifo usando <xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun>. No entanto, o custo dessa eficiência é a perda de formatação de Rich Text fácil de usar, que são recursos internos de controles de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], como <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Objeto FormattedText

O objeto <xref:System.Windows.Media.FormattedText> permite desenhar texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. Para mais informações, consulte [Desenhando texto formatado](drawing-formatted-text.md).

Para criar texto formatado, chame o Construtor <xref:System.Windows.Media.FormattedText.%23ctor%2A> para criar um objeto <xref:System.Windows.Media.FormattedText>. Após ter criado a cadeia de caracteres de texto formatado inicial, você poderá aplicar uma variedade de estilos de formatação. Se o seu aplicativo quiser implementar seu próprio layout, o objeto <xref:System.Windows.Media.FormattedText> será melhor escolha do que usar um controle, como <xref:System.Windows.Controls.TextBlock>. Para obter mais informações sobre o objeto <xref:System.Windows.Media.FormattedText>, consulte [desenho de texto formatado](drawing-formatted-text.md) .

O objeto <xref:System.Windows.Media.FormattedText> fornece a funcionalidade de formatação de texto de baixo nível. É possível aplicar vários estilos de formatação a um ou mais caracteres. Por exemplo, você pode chamar os métodos <xref:System.Windows.Media.FormattedText.SetFontSize%2A> e <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> para alterar a formatação dos cinco primeiros caracteres no texto.

O exemplo de código a seguir cria um objeto <xref:System.Windows.Media.FormattedText> e o renderiza.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Controles de rótulo, TextBlock e FlowDocument

O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>O FlowDocument impacta o desempenho mais do que o TextBlock ou o Rótulo

Em geral, o elemento <xref:System.Windows.Controls.TextBlock> deve ser usado quando o suporte a texto limitado é necessário, como uma breve frase em uma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> pode ser usado quando o suporte a texto mínimo é necessário. O elemento <xref:System.Windows.Documents.FlowDocument> é um contêiner para documentos refluíáveis que dão suporte à apresentação avançada de conteúdo e, portanto, tem um impacto maior no desempenho do que usar os controles <xref:System.Windows.Controls.TextBlock> ou <xref:System.Windows.Controls.Label>.

Para obter mais informações sobre <xref:System.Windows.Documents.FlowDocument>, consulte [visão geral do documento de fluxo](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Evite usar TextBlock em FlowDocument

O elemento <xref:System.Windows.Controls.TextBlock> é derivado de <xref:System.Windows.UIElement>. O elemento <xref:System.Windows.Documents.Run> é derivado de <xref:System.Windows.Documents.TextElement>, que é menos dispendioso para ser usado do que um objeto derivado de <xref:System.Windows.UIElement>. Quando possível, use <xref:System.Windows.Documents.Run> em vez de <xref:System.Windows.Controls.TextBlock> para exibir o conteúdo de texto em um <xref:System.Windows.Documents.FlowDocument>.

O exemplo de marcação a seguir ilustra duas maneiras de definir o conteúdo de texto em um <xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Evite usar Run para definir propriedades de texto

Em geral, o uso de um <xref:System.Windows.Documents.Run> dentro de um <xref:System.Windows.Controls.TextBlock> é mais intensivo em desempenho do que não usar um objeto <xref:System.Windows.Documents.Run> explícito. Se você estiver usando um <xref:System.Windows.Documents.Run> para definir propriedades de texto, defina essas propriedades diretamente na <xref:System.Windows.Controls.TextBlock> em vez disso.

O exemplo de marcação a seguir ilustra essas duas maneiras de definir uma propriedade de texto, nesse caso, a propriedade <xref:System.Windows.Controls.TextBlock.FontWeight%2A>:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

A tabela a seguir mostra o custo da exibição de 1000 <xref:System.Windows.Controls.TextBlock> objetos com e sem uma <xref:System.Windows.Documents.Run>explícita.

|**Tipo TextBlock**|**Tempo de criação (ms)**|**Tempo de renderização (ms)**|
|------------------------|------------------------------|----------------------------|
|Propriedades de texto de configuração Run|146|540|
|Propriedades de texto de configuração TextBlock|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Evite a associação de dados com a propriedade Label.Content

Imagine um cenário em que você tenha um objeto <xref:System.Windows.Controls.Label> que é atualizado com frequência de uma fonte de <xref:System.String>. Quando os dados são vinculados à propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> do elemento de <xref:System.Windows.Controls.Label> para o objeto de origem <xref:System.String>, você pode experimentar um desempenho insatisfatório. Cada vez que o <xref:System.String> de origem é atualizado, o objeto <xref:System.String> antigo é Descartado e uma nova <xref:System.String> é recriada — como um objeto <xref:System.String> é imutável, ele não pode ser modificado. Isso, por sua vez, faz com que o <xref:System.Windows.Controls.ContentPresenter> do objeto <xref:System.Windows.Controls.Label> descarte seu conteúdo antigo e gere novamente o novo conteúdo para exibir o novo <xref:System.String>.

A solução para esse problema é simples. Se o <xref:System.Windows.Controls.Label> não estiver definido como um valor de <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> personalizado, substitua o <xref:System.Windows.Controls.Label> por um <xref:System.Windows.Controls.TextBlock> e vincule os dados à sua propriedade <xref:System.Windows.Controls.TextBlock.Text%2A> para a cadeia de caracteres de origem.

|**Propriedade associada de dados**|**Tempo de atualização (ms)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Hiperlink

O objeto <xref:System.Windows.Documents.Hyperlink> é um elemento de conteúdo de fluxo de nível embutido que permite hospedar hiperlinks dentro do conteúdo do fluxo.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Combinando hiperlinks em um objeto TextBlock

Você pode otimizar o uso de vários elementos de <xref:System.Windows.Documents.Hyperlink> agrupando-os em conjunto no mesmo <xref:System.Windows.Controls.TextBlock>. Isso ajuda a minimizar o número de objetos criados em seu aplicativo. Por exemplo, você talvez queira exibir vários hiperlinks, como o seguinte:

Página inicial do MSN &#124; Meu MSN

O exemplo de marcação a seguir mostra vários elementos <xref:System.Windows.Controls.TextBlock> usados para exibir os hiperlinks:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

O exemplo de marcação a seguir mostra uma maneira mais eficiente de exibir os hiperlinks, desta vez, usando uma única <xref:System.Windows.Controls.TextBlock>:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Mostrando sublinhados em hiperlinks somente em eventos MouseEnter

Um objeto <xref:System.Windows.TextDecoration> é um ornamento visual que você pode adicionar ao texto; no entanto, pode haver um desempenho intensivo para criar uma instância. Se você fizer uso extensivo de elementos <xref:System.Windows.Documents.Hyperlink>, considere mostrar um sublinhado somente ao disparar um evento, como o evento <xref:System.Windows.ContentElement.MouseEnter>. Para obter mais informações, consulte [Especificar se um hiperlink está sublinhado](how-to-specify-whether-a-hyperlink-is-underlined.md).

A imagem a seguir mostra como o evento MouseEnter dispara o hiperlink sublinhado:

![Hiperlinks exibindo TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

O exemplo de marcação a seguir mostra um <xref:System.Windows.Documents.Hyperlink> definido com e sem um sublinhado:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

A tabela a seguir mostra o custo de desempenho da exibição de 1000 <xref:System.Windows.Documents.Hyperlink> elementos com e sem um sublinhado.

|**Hiperlink**|**Tempo de criação (ms)**|**Tempo de renderização (ms)**|
|-------------------|------------------------------|----------------------------|
|Com sublinhado|289|1130|
|Sem sublinhado|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Recursos de formatação de texto

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece serviços de formatação de texto avançado, como hifenizações automáticas. Esses serviços podem afetar o desempenho do aplicativo e devem ser usados somente quando necessário.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Evite o uso desnecessário de hifenização

A hifenização automática localiza pontos de interrupção de hífen para linhas de texto e permite posições de quebra adicionais para linhas em objetos <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument>. Por padrão, o recurso de hifenização automática está desabilitado nesses objetos. Você pode habilitar esse recurso configurando a propriedade IsHyphenationEnabled do objeto como `true`. No entanto, habilitar esse recurso faz com que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inicie a interoperabilidade Component Object Model (COM), o que pode afetar o desempenho do aplicativo. É recomendável que você não use a hifenização automática, a menos que necessário.

### <a name="use-figures-carefully"></a>Use as figuras com cuidado

Um elemento <xref:System.Windows.Documents.Figure> representa uma parte do conteúdo do fluxo que pode ser absolutamente posicionado em uma página de conteúdo. Em alguns casos, um <xref:System.Windows.Documents.Figure> pode fazer com que uma página inteira reformate automaticamente se sua posição colide com o conteúdo que já foi definido. Você pode minimizar a possibilidade de reformatação desnecessária agrupando <xref:System.Windows.Documents.Figure> elementos ao lado um do outro, ou declará-los perto da parte superior do conteúdo em um cenário de tamanho fixo de página.

### <a name="optimal-paragraph"></a>Parágrafo ideal

O recurso de parágrafo ideal do objeto <xref:System.Windows.Documents.FlowDocument> apresenta parágrafos para que o espaço em branco seja distribuído da maneira mais uniforme possível. Por padrão, o recurso de parágrafo otimizado é desabilitado. Você pode habilitar esse recurso definindo a propriedade de <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> do objeto como `true`. No entanto, habilitar esse recurso afeta o desempenho do aplicativo. É recomendável que você não use o recurso de parágrafo ideal, a menos que necessário.

## <a name="see-also"></a>Veja também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
