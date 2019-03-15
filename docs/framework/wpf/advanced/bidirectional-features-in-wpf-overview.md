---
title: Visão geral dos recursos bidirecionais no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 12ca85132ca063471092078c6f54e23a57f574ae
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846435"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Visão geral dos recursos bidirecionais no WPF
Ao contrário de qualquer outra plataforma de desenvolvimento, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem muitos recursos que dão suporte ao desenvolvimento rápido de conteúdo bidirecional, por exemplo, mistos da esquerda para a direita e da direita para esquerda dados no mesmo documento. Ao mesmo tempo, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria uma excelente experiência para usuários que exigem recursos bidirecionais, como árabe e hebraico, falando em usuários.  
  
 As próximas seções explicam vários recursos bidirecionais junto com exemplos que ilustram como obter a melhor exibição do conteúdo bidirecional. A maioria dos exemplos usa [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], que você pode facilmente aplicar os conceitos para C# ou o código do Microsoft Visual Basic.  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 A propriedade básica que define a direção do fluxo de conteúdo em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo é <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Essa propriedade pode ser definida como um dos dois valores de enumeração <xref:System.Windows.FlowDirection.LeftToRight> ou <xref:System.Windows.FlowDirection.RightToLeft>. A propriedade está disponível para todos os [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos que herdam de <xref:System.Windows.FrameworkElement>.  
  
 Os exemplos a seguir definem a direção do fluxo de um <xref:System.Windows.Controls.TextBox> elemento.  
  
 **Direção do fluxo da esquerda para a direita**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Direção do fluxo da direita para a esquerda**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 O gráfico a seguir mostra como o código anterior é renderizado.  
    
 ![Gráfico que ilustra as direções de fluxo diferentes.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 Um elemento dentro de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] árvore herdará o <xref:System.Windows.FrameworkElement.FlowDirection%2A> de seu contêiner. No exemplo a seguir, o <xref:System.Windows.Controls.TextBlock> está dentro de uma <xref:System.Windows.Controls.Grid>, que reside em um <xref:System.Windows.Window>. Definindo o <xref:System.Windows.FrameworkElement.FlowDirection%2A> para o <xref:System.Windows.Window> implica defini-lo para o <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Controls.TextBlock> também.  
  
 O exemplo a seguir demonstra a configuração <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 O nível superior <xref:System.Windows.Window> tem uma <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, de modo que todos os elementos contidos nela também herdam o mesmo <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Para um elemento substitua uma especificado <xref:System.Windows.FrameworkElement.FlowDirection%2A> ele deve adicionar uma mudança de direção explícita como o segundo <xref:System.Windows.Controls.TextBlock> no exemplo anterior que altera para <xref:System.Windows.FlowDirection.LeftToRight>. Quando nenhum <xref:System.Windows.FrameworkElement.FlowDirection%2A> for definido, o padrão <xref:System.Windows.FlowDirection.LeftToRight> se aplica.  
  
 O gráfico a seguir mostra a saída do exemplo anterior:

 ![Gráfico que ilustra a mudança de direção de fluxo explícito.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Muitas plataformas de desenvolvimento, como [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e Java fornecem suporte especial para o desenvolvimento de conteúdo bidirecional. Linguagens de marcação, como [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dar criadores de conteúdo a marcação necessária para exibir o texto em uma direção necessária, por exemplo o [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 tag, "dir" que usa "rtl" ou "ltr" como valores. Essa marca é semelhante do <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade, mas o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade funciona de maneira mais avançada para conteúdo textual do layout e pode ser usada para o conteúdo que não sejam de texto.  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], um <xref:System.Windows.Documents.FlowDocument> é um versátil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento que pode hospedar uma combinação de texto, tabelas, imagens e outros elementos. As amostras das próximas seções usam esse elemento.  
  
 Adicionando texto a um <xref:System.Windows.Documents.FlowDocument> pode ser feito em mais de uma maneira. Uma maneira simples de fazer isso é por meio de um <xref:System.Windows.Documents.Paragraph> que é um elemento de nível de bloco usado para agrupar conteúdo como texto. Para adicionar texto ao usam os exemplos de elementos de nível incorporado <xref:System.Windows.Documents.Span> e <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> é um elemento de conteúdo de fluxo de nível embutido usado para agrupar outros elementos embutidos, enquanto um <xref:System.Windows.Documents.Run> é um fluxo de nível embutido conteúdo de elemento deve conter uma sequência de texto não formatado. Um <xref:System.Windows.Documents.Span> pode conter vários <xref:System.Windows.Documents.Run> elementos.  
  
 O primeiro exemplo de documento contém um documento que tem um número de rede a compartilhar nomes; Por exemplo `\\server1\folder\file.ext`. Se você tiver esse link de rede em um documento em árabe ou em inglês, você sempre desejará que ele seja exibido da mesma maneira. O gráfico a seguir ilustra como usar o elemento Span e mostra o link em um árabe <xref:System.Windows.FlowDirection.RightToLeft> documento:

 ![Gráfico que ilustra usando o elemento de intervalo. ](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 Como o texto é <xref:System.Windows.FlowDirection.RightToLeft>especial todos os caracteres, como o "\\", separam o texto em uma ordem da direita para esquerda. O resultado é o link não seja mostrado na ordem correta, portanto para resolver o problema, o texto deve ser inserido para preservar um separado <xref:System.Windows.Documents.Run> fluindo <xref:System.Windows.FlowDirection.LeftToRight>. Em vez de ter um separado <xref:System.Windows.Documents.Run> para cada idioma, uma maneira melhor para resolver o problema é inserir o texto em inglês usado com menos frequência em uma maior em árabe <xref:System.Windows.Documents.Span>.  
  
 O gráfico a seguir ilustra isso usando o elemento de execução incorporado em um elemento Span:

 ![Gráfico que ilustra o elemento de execução é inserido em um elemento Span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 O exemplo a seguir demonstra como usar <xref:System.Windows.Documents.Run> e <xref:System.Windows.Documents.Span> elementos em documentos.  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Elementos de extensão  
 O <xref:System.Windows.Documents.Span> elemento funciona como um separador de limite entre textos com direções de fluxo diferentes.  Até mesmo <xref:System.Windows.Documents.Span> elementos com a mesma direção de fluxo são considerados como tendo escopos bidirecionais diferentes, que significa que o <xref:System.Windows.Documents.Span> elementos serão ordenados no contêiner de <xref:System.Windows.FlowDirection>, somente o conteúdo dentro do <xref:System.Windows.Documents.Span> elemento segue o <xref:System.Windows.FlowDirection> do <xref:System.Windows.Documents.Span>.  
  
 O gráfico a seguir mostra a direção do fluxo de vários <xref:System.Windows.Controls.TextBlock> elementos.  
    
 ![Gráfico que ilustra blocos de texto com direções de fluxo diferentes.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Documents.Span> e <xref:System.Windows.Documents.Run> elementos para produzir os resultados mostrados no gráfico anterior.  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 No <xref:System.Windows.Controls.TextBlock> elementos no exemplo, o <xref:System.Windows.Documents.Span> elementos são dispostos de acordo com as <xref:System.Windows.FlowDirection> de seus pais, mas o texto dentro de cada <xref:System.Windows.Documents.Span> fluxos de elemento de acordo com seu próprio <xref:System.Windows.FlowDirection>. Isso é aplicável ao latim e ao árabe – ou a qualquer outro idioma.  
  
### <a name="adding-xmllang"></a>Adicionando xml:lang  
 O gráfico a seguir mostra outro exemplo que usa números e expressões aritméticas, como `"200.0+21.4=221.4"`. Observe que somente o <xref:System.Windows.FlowDirection> está definido.  
    
 ![Gráfico que exibe números usando apenas a FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 Os usuários desse aplicativo serão desapontados pela saída, mesmo que o <xref:System.Windows.FlowDirection> está correta, os números não são formatados como números em árabe devem ter a forma.  
  
 Elementos XAML podem incluir um [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atributo (`xml:lang`) que define o idioma de cada elemento. XAML também dá suporte a um [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] princípio de idioma no qual `xml:lang` aplicados aos elementos pai na árvore de valores são usados pelos elementos filho. No exemplo anterior, porque um idioma não foi definido para o <xref:System.Windows.Documents.Run> elementos, o padrão de nível de elemento ou qualquer um dos seus principais `xml:lang` tiver sido usado, que é `en-US` para XAML. O algoritmo de formatação numérico interno do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] seleciona números no idioma correspondente – nesse caso, em inglês. Para tornar o árabe números renderização corretamente `xml:lang` precisa ser definido.  
  
 O gráfico a seguir mostra o exemplo com `xml:lang` adicionado.  
    
 ![Gráfico que ilustra números em árabe que fluem da direita para esquerda.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 O exemplo a seguir adiciona `xml:lang` ao aplicativo.  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Lembre-se de que muitos idiomas têm diferentes `xml:lang` valores, dependendo da região direcionada, por exemplo, `"ar-SA"` e `"ar-EG"` representam duas variações do árabe. Os exemplos anteriores ilustram que você precisa definir ambos os `xml:lang` e <xref:System.Windows.FlowDirection> valores.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection com elementos não texto  
 <xref:System.Windows.FlowDirection> Define não apenas como o texto flui em um elemento textual, mas também a direção do fluxo de quase todos os outros [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento. A gráfico a seguir mostra uma <xref:System.Windows.Controls.ToolBar> que usa um horizontal <xref:System.Windows.Media.LinearGradientBrush> para desenhar seu plano de fundo com da esquerda para direita gradiente.  

 ![Gráfico que mostra uma barra de ferramentas com da esquerda para direita gradiente.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 Depois de definir a <xref:System.Windows.FlowDirection> à <xref:System.Windows.FlowDirection.RightToLeft>, não apenas o <xref:System.Windows.Controls.ToolBar> botões são dispostos da direita para a esquerda, mas até mesmo o <xref:System.Windows.Media.LinearGradientBrush> realinha seus deslocamentos para fluir da direita para a esquerda.  
  
 O gráfico a seguir mostra o realinhamento do <xref:System.Windows.Media.LinearGradientBrush>.  
    
 ![Gráfico que mostra uma barra de ferramentas com um direito de gradiente à esquerda.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 O exemplo a seguir desenha uma <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Para desenhá-la à esquerda para a direita, remova os <xref:System.Windows.FlowDirection> atributo a <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Exceções de FlowDirection  
 Há alguns casos em que <xref:System.Windows.FlowDirection> não se comportar conforme o esperado. Esta seção aborda duas dessas exceções.  
  
 **Image**  
  
 Um <xref:System.Windows.Controls.Image> representa um controle que exibe uma imagem. Na [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ele pode ser usado com um <xref:System.Windows.Controls.Image.Source%2A> propriedade que define o [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] da <xref:System.Windows.Controls.Image> para exibir.  
  
 Ao contrário de outras [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos, uma <xref:System.Windows.Controls.Image> não herda o <xref:System.Windows.FlowDirection> do contêiner. No entanto, se o <xref:System.Windows.FlowDirection> é definido explicitamente como <xref:System.Windows.FlowDirection.RightToLeft>, um <xref:System.Windows.Controls.Image> será exibida invertida horizontalmente. Isso é implementado como um recurso conveniente para desenvolvedores de conteúdo bidirecional, pois, em alguns casos, inverter a imagem horizontalmente produz o efeito desejado.  
  
 O gráfico a seguir mostra um invertida <xref:System.Windows.Controls.Image>.  
    
 ![Gráfico que ilustra uma imagem invertida.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 O exemplo a seguir demonstra que o <xref:System.Windows.Controls.Image> não herda de <xref:System.Windows.FlowDirection> do <xref:System.Windows.Controls.StackPanel> que o contém. **Observação** você deve ter um arquivo chamado **ms_logo** em seu c:\. unidade para executar este exemplo.  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Observação** incluído no download de arquivos é um **ms_logo** arquivo. O código pressupõe que o arquivo .jpg não está dentro do projeto, mas em algum lugar na unidade C:\. É necessário copiar o .jpg dos arquivos de projeto para a unidade C:\ ou alterar o código para procurar o arquivo dentro do projeto. Para fazer isso, altere `Source="file://c:/ms_logo.jpg"` para `Source="ms_logo.jpg"`.  
  
 **Caminhos**  
  
 Além de um <xref:System.Windows.Controls.Image>, outro elemento interessante é <xref:System.Windows.Shapes.Path>. Um Caminho é um objeto que pode desenhar uma série de linhas e curvas conectadas. Ele se comporta de maneira semelhante a um <xref:System.Windows.Controls.Image> em relação ao seu <xref:System.Windows.FlowDirection>; por exemplo seu <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> é um espelho horizontal de seu <xref:System.Windows.FlowDirection.LeftToRight> um. No entanto, ao contrário de um <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> herda seu <xref:System.Windows.FlowDirection> do contêiner e um não precisa especificá-lo explicitamente.  
  
 O exemplo a seguir desenha uma seta simples usando 3 linhas. A primeira seta herda a <xref:System.Windows.FlowDirection.RightToLeft> direção de fluxo de <xref:System.Windows.Controls.StackPanel> para que seus pontos inicial e final são medidos a partir de uma raiz no lado direito. A segunda seta que tem um explícito <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> também começa no lado direito. No entanto, a terceira seta tem sua raiz inicial no lado esquerdo. Para obter mais informações sobre desenho, consulte <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 O gráfico a seguir mostra a saída do exemplo anterior com setas desenhadas com o `Path` elemento:

 ![Gráfico que ilustra setas desenhadas com o elemento de caminho.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 O <xref:System.Windows.Controls.Image> e <xref:System.Windows.Shapes.Path> são dois exemplos de como [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] usa <xref:System.Windows.FlowDirection>. Além de dispor os [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos em uma direção específica dentro de um contêiner <xref:System.Windows.FlowDirection> tais como pode ser usado com elementos <xref:System.Windows.Controls.InkPresenter> que renderiza a tinta em uma superfície <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Sempre que você precisa de um direito de comportamento à esquerda para o conteúdo que imita da esquerda para direita comportamento, ou vice-versa, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece esse recurso.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Substituição de números  
 Historicamente, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] tem suporte para a substituição de números, permitindo a representação de diferentes formas culturais para os mesmos dígitos, mantendo o armazenamento interno desses dígitos unificado entre localidades diferentes, para números de exemplo são armazenados em seus valores hexadecimais conhecidos, 0x40, 0x41, mas exibidos de acordo com o idioma selecionado.  
  
 Isso permite aos aplicativos processar valores numéricos sem a necessidade de convertê-los de um idioma para outro, por exemplo, um usuário pode abrir um [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] planilha em um árabe [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e ver os números formatados em árabe, mas abri-lo no uma versão europeia do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e ver a representação Europeia dos mesmos números. Isso também é necessário para outros símbolos, como separadores de vírgula e símbolo de percentual, porque eles geralmente acompanham os números no mesmo documento.  
  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dá continuidade à mesma tradição e adiciona suporte adicional a esse recurso, o que permite maior controle do usuário sobre quando e como a substituição é usada. Embora esse recurso tenha sido projetado para qualquer idioma, ele é particularmente útil no conteúdo bidirecional, em que a formatação de dígitos de um idioma específico é, de modo geral, um desafio para os desenvolvedores de aplicativos, devido às várias culturas nas quais um aplicativo pode ser executado.  
  
 A propriedade do principal que controla a substituição de números como funciona [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é o <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade de dependência. O <xref:System.Windows.Media.NumberSubstitution> classe especifica como os números no texto devem ser exibidos. Ela tem três propriedades públicas que definem seu comportamento. Veja a seguir um resumo de cada uma das propriedades.  
  
 **CultureSource:**  
  
 Essa propriedade especifica como a cultura para números é determinada. Ela usa um dos três <xref:System.Windows.Media.NumberCultureSource> valores de enumeração.  
  
-   Substituição: Cultura de número é o de <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriedade.  
  
-   Texto: Cultura de número é a cultura da sequência de texto. Na marcação, isso seria `xml:lang`, ou seu alias `Language` propriedade (<xref:System.Windows.FrameworkElement.Language%2A> ou <xref:System.Windows.FrameworkContentElement.Language%2A>). Além disso, ele é o padrão para classes derivadas de <xref:System.Windows.FrameworkContentElement>. Essas classes incluem <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> e assim por diante.  
  
-   Usuário: Cultura de número é a cultura do thread atual. Essa propriedade é o padrão para todas as subclasses da <xref:System.Windows.FrameworkElement> , como <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> e <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 O <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriedade é usada somente se o <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> estiver definida como <xref:System.Windows.Media.NumberCultureSource.Override> e será ignorada caso contrário. Ela especifica a cultura dos números. Um valor de `null`, o valor padrão, é interpretado como en-US.  
  
 **Substitution**:  
  
 Essa propriedade especifica o tipo de substituição de números a ser executado. Ela usa um dos seguintes <xref:System.Windows.Media.NumberSubstitutionMethod> valores de enumeração.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: O método de substituição é determinado com base na cultura de número <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> propriedade. Esse é o padrão.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Se a cultura dos números for uma cultura árabe ou persa, especifica que os dígitos dependem do contexto.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Números sempre são renderizados como dígitos europeus.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Os números são renderizados usando os dígitos nacionais da cultura dos números, conforme especificado pela cultura do <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Números são renderizados usando os dígitos tradicionais para a cultura de número. Na maioria das culturas, isso é o mesmo que <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. No entanto, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> resulta em dígitos latinos para algumas culturas árabes, enquanto esse valor resulta em dígitos árabes para todas as culturas árabes.  
  
 O que esses valores significam para um desenvolvedor de conteúdo bidirecional? Na maioria dos casos, o desenvolvedor pode precisar apenas definir <xref:System.Windows.FlowDirection> e o idioma de cada textual [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento, por exemplo `Language="ar-SA"` e o <xref:System.Windows.Media.NumberSubstitution> lógica se encarrega de exibir os números de acordo com o correto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O exemplo a seguir demonstra o uso de números em árabe e inglês em um [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativo em execução em uma versão em árabe do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 O gráfico a seguir mostra a saída do exemplo anterior, se você estiver executando uma versão em árabe do Windows com números em árabe e inglês exibidos:

 ![Gráfico que mostra os números em árabe e inglês.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 O <xref:System.Windows.FlowDirection> era importante nesse caso, porque a definição de <xref:System.Windows.FlowDirection> para <xref:System.Windows.FlowDirection.LeftToRight> produziria dígitos europeus. As próximas seções abordam como ter uma exibição unificada de dígitos em todo o documento. Se esse exemplo não estiver sendo executado no Windows em árabe, todos os dígitos serão exibidos como dígitos europeus.  
  
 **Definindo regras de substituição**  
  
 Em um aplicativo real, talvez você deseje definir o Idioma de forma programática. Por exemplo, você deseja definir a `xml:lang` atributo a ser o mesmo que aquele usado pelo sistema de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ou talvez alterar o idioma, dependendo do estado do aplicativo.  
  
 Se você quiser fazer alterações de acordo com o estado do aplicativo, faça uso de outros recursos fornecidos pelo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Primeiro, defina o componente de aplicativo `NumberSubstitution.CultureSource="Text"`. Usar essa configuração garante que as configurações não vêm dos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dos elementos de texto que contêm "Usuário" como padrão, como <xref:System.Windows.Controls.TextBlock>.  
  
Por exemplo:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

Na C# de código, defina a `Language` propriedade, por exemplo, para `"ar-SA"`.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Se você precisar definir o `Language` propriedade para o idioma da interface do usuário atual usar o código a seguir.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> representa a cultura atual usada pelo thread atual em tempo de execução.  
  
 Final [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] exemplo deve ser semelhante ao exemplo a seguir.  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Seu último C# exemplo deve ser semelhante ao seguinte.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 O gráfico a seguir mostra a aparência de janela para qualquer linguagem de programação, exibindo os números em árabe:
     
 ![Gráfico que exibe números em árabe.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **Usando a propriedade de substituição**  
  
 A substituição de número de forma funciona no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] depende do idioma do elemento de texto e seu <xref:System.Windows.FlowDirection>. Se o <xref:System.Windows.FlowDirection> é da esquerda para direita, em seguida, dígitos europeus serão renderizados. No entanto se ele é precedido pelo texto em árabe ou tiver o idioma definido como "ar" e o <xref:System.Windows.FlowDirection> é <xref:System.Windows.FlowDirection.RightToLeft>, dígitos árabes são renderizados em vez disso.  
  
 No entanto, em alguns casos, talvez você deseje criar um aplicativo unificado, por exemplo, europeus dígitos para todos os usuários. Ou dígitos em árabe <xref:System.Windows.Documents.Table> células com um determinado <xref:System.Windows.Style>. Uma maneira fácil de fazer o que está usando o <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade.  
  
 No exemplo a seguir, a primeira <xref:System.Windows.Controls.TextBlock> não tem o <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade definida, portanto, o algoritmo exibe dígitos árabes como esperado. No entanto no segundo <xref:System.Windows.Controls.TextBlock>, a substituição está definida como Europeu, substituindo a substituição padrão para números em árabe e dígitos europeus são exibidos.  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
