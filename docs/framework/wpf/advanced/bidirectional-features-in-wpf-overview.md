---
title: Visão geral dos recursos bidirecionais no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: d2b35a50d9d09bffd69ae8b8217d6e778ce66ea0
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796409"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Visão geral dos recursos bidirecionais no WPF
Ao contrário de qualquer outra plataforma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de desenvolvimento, o tem muitos recursos que dão suporte ao desenvolvimento rápido de conteúdo bidirecional, por exemplo, misto da esquerda para a direita e da direita para a esquerda dos dados no mesmo documento. Ao mesmo tempo, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o cria uma experiência excelente para os usuários que precisam de recursos bidirecionais, como o árabe e o Hebraico falando de usuários.  
  
 As próximas seções explicam vários recursos bidirecionais junto com exemplos que ilustram como obter a melhor exibição do conteúdo bidirecional. A maioria dos exemplos é [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]usada, embora você possa facilmente aplicar os conceitos C# ao ou ao Microsoft Visual Basic Code.  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 A propriedade básica que define a direção do fluxo de conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um <xref:System.Windows.FrameworkElement.FlowDirection%2A>aplicativo é. Essa propriedade pode ser definida como um dos dois valores <xref:System.Windows.FlowDirection.LeftToRight> de enumeração ou. <xref:System.Windows.FlowDirection.RightToLeft> A propriedade está disponível para todos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os elementos que herdam de. <xref:System.Windows.FrameworkElement>  
  
 Os exemplos a seguir definem a direção do <xref:System.Windows.Controls.TextBox> fluxo de um elemento.  
  
 **Direção do fluxo da esquerda para a direita**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Direção do fluxo da direita para a esquerda**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 O gráfico a seguir mostra como o código anterior é renderizado.  
    
 ![Gráfico que ilustra as diferentes direções de fluxo.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 Um elemento dentro de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uma árvore herdará <xref:System.Windows.FrameworkElement.FlowDirection%2A> o de seu contêiner. No exemplo a seguir, o <xref:System.Windows.Controls.TextBlock> está dentro de <xref:System.Windows.Controls.Grid>um, que reside em um <xref:System.Windows.Window>. Definir o <xref:System.Windows.FrameworkElement.FlowDirection%2A> para o <xref:System.Windows.Window> implica defini-lo para <xref:System.Windows.Controls.Grid> o <xref:System.Windows.Controls.TextBlock> e também.  
  
 O exemplo a seguir demonstra <xref:System.Windows.FrameworkElement.FlowDirection%2A>a configuração.  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 O nível <xref:System.Windows.Window> superior tem um <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, portanto, todos os elementos contidos nele também herdam <xref:System.Windows.FrameworkElement.FlowDirection%2A>o mesmo. Para que um elemento substitua um especificado <xref:System.Windows.FrameworkElement.FlowDirection%2A> , ele deve adicionar uma alteração de direção explícita, como <xref:System.Windows.Controls.TextBlock> a segunda no exemplo anterior, que <xref:System.Windows.FlowDirection.LeftToRight>muda para. Quando não <xref:System.Windows.FrameworkElement.FlowDirection%2A> estiver definido, o padrão <xref:System.Windows.FlowDirection.LeftToRight> será aplicável.  
  
 O gráfico a seguir mostra a saída do exemplo anterior:

 ![Gráfico que ilustra a alteração da direção do fluxo explícito.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Muitas plataformas de desenvolvimento, como HTML [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] , e Java fornecem suporte especial para o desenvolvimento de conteúdo bidirecional. As linguagens de marcação, como HTML, dão aos gravadores de conteúdo a marcação necessária para exibir texto em qualquer direção necessária, por exemplo, a marca HTML 4,0, "dir" que usa "RTL" ou "EPD" como valores. Essa marca é semelhante à <xref:System.Windows.FrameworkElement.FlowDirection%2A> Propriedade, mas a <xref:System.Windows.FrameworkElement.FlowDirection%2A> Propriedade funciona de forma mais avançada para layout de conteúdo textual e pode ser usada para conteúdo que não seja texto.  
  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], um <xref:System.Windows.Documents.FlowDocument> é um elemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] versátil que pode hospedar uma combinação de texto, tabelas, imagens e outros elementos. As amostras das próximas seções usam esse elemento.  
  
 Adicionar texto a um <xref:System.Windows.Documents.FlowDocument> pode ser feito de forma mais unidirecional. Uma maneira simples de fazer isso é por meio <xref:System.Windows.Documents.Paragraph> de um que é um elemento de nível de bloco usado para agrupar conteúdo, como texto. Para adicionar texto a elementos de nível embutido, os <xref:System.Windows.Documents.Span> exemplos <xref:System.Windows.Documents.Run>usam e. <xref:System.Windows.Documents.Span>é um elemento de conteúdo de fluxo de nível embutido usado para agrupar outros elementos embutidos, enquanto um <xref:System.Windows.Documents.Run> é um elemento de conteúdo de fluxo de nível embutido destinado a conter uma execução de texto não formatado. Um <xref:System.Windows.Documents.Span> pode conter vários <xref:System.Windows.Documents.Run> elementos.  
  
 O primeiro exemplo de documento contém um documento que tem um número de nomes de compartilhamento de rede; por exemplo `\\server1\folder\file.ext`,. Se você tiver esse link de rede em um documento em árabe ou em inglês, você sempre desejará que ele seja exibido da mesma maneira. O gráfico a seguir ilustra o uso do elemento span e mostra o link em <xref:System.Windows.FlowDirection.RightToLeft> um documento em árabe:

 ![Gráfico que ilustra o uso do elemento span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 Como o texto é <xref:System.Windows.FlowDirection.RightToLeft>, todos os caracteres especiais, como "\\", separam o texto em uma ordem direita para a esquerda. Isso faz com que o link não seja mostrado na ordem correta, portanto, para resolver o problema, o texto deve ser inserido para preservar um <xref:System.Windows.Documents.Run> fluxo <xref:System.Windows.FlowDirection.LeftToRight>separado. Em vez de ter um <xref:System.Windows.Documents.Run> separado para cada idioma, uma maneira melhor de resolver o problema é inserir o texto em inglês com menos frequência em um árabe <xref:System.Windows.Documents.Span>maior.  
  
 O gráfico a seguir ilustra isso usando o elemento Run inserido em um elemento span:

 ![Gráfico que ilustra o elemento Run inserido em um elemento span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 O exemplo a seguir demonstra <xref:System.Windows.Documents.Run> o <xref:System.Windows.Documents.Span> uso de elementos e em documentos.  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Elementos de extensão  
 O <xref:System.Windows.Documents.Span> elemento funciona como um separador de limite entre textos com direções de fluxo diferentes.  Até <xref:System.Windows.Documents.Span> mesmo elementos com a mesma direção de fluxo são considerados com escopos bidirecionais diferentes <xref:System.Windows.Documents.Span> <xref:System.Windows.FlowDirection>, o que significa que os elementos são ordenados no contêiner, <xref:System.Windows.Documents.Span> somente o conteúdo dentro do elemento segue o <xref:System.Windows.FlowDirection> <xref:System.Windows.Documents.Span>do.  
  
 O gráfico a seguir mostra a direção do fluxo <xref:System.Windows.Controls.TextBlock> de vários elementos.  
    
 ![Gráfico que ilustra os blocos de texto com direções de fluxo diferentes.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 O exemplo a seguir mostra como usar os <xref:System.Windows.Documents.Span> elementos <xref:System.Windows.Documents.Run> e para produzir os resultados mostrados no gráfico anterior.  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> <xref:System.Windows.Documents.Span> Nos elementos no exemplo, os <xref:System.Windows.Documents.Span> elementos são dispostos de acordo com o de seus pais, mas o texto dentro de cada elemento flui de acordo com o seu próprio. <xref:System.Windows.Controls.TextBlock> Isso é aplicável ao latim e ao árabe – ou a qualquer outro idioma.  
  
### <a name="adding-xmllang"></a>Adicionando xml:lang  
 O gráfico a seguir mostra outro exemplo que usa números e expressões aritméticas, `"200.0+21.4=221.4"`como. Observe que apenas o <xref:System.Windows.FlowDirection> é definido.  
    
 ![Gráfico que exibe números usando apenas FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 Os usuários desse aplicativo serão desapontados pela saída, mesmo que o <xref:System.Windows.FlowDirection> esteja correto, os números não sejam formatados como números árabes devem ser formatados.  
  
 Os elementos XAML podem incluir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] um atributo`xml:lang`() que define o idioma de cada elemento. O XAML também dá [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] suporte a um `xml:lang` princípio de linguagem no qual os valores aplicados aos elementos pai na árvore são usados por elementos filho. No exemplo anterior, como um idioma não foi definido para o <xref:System.Windows.Documents.Run> elemento ou qualquer um de seus elementos de nível superior, o padrão `xml:lang` foi usado, que `en-US` é para XAML. O algoritmo de formatação de número [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] interno do seleciona números no idioma correspondente – neste caso, inglês. Para fazer com que os números árabes `xml:lang` sejam processados corretamente, é necessário definir.  
  
 O gráfico a seguir mostra o exemplo `xml:lang` com adicionado.  
    
 ![Gráfico que ilustra os números árabes que fluem da direita para a esquerda.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 O exemplo a seguir `xml:lang` adiciona ao aplicativo.  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Lembre-se de que muitas linguagens têm valores diferentes `xml:lang` dependendo da região de destino, por exemplo, `"ar-SA"` e `"ar-EG"` representam duas variações de árabe. Os exemplos anteriores ilustram que você precisa definir os `xml:lang` valores e. <xref:System.Windows.FlowDirection>  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection com elementos não texto  
 <xref:System.Windows.FlowDirection>define não apenas como o texto flui em um elemento textual, mas também a direção do fluxo de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] quase todos os outros elementos. O gráfico a seguir mostra <xref:System.Windows.Controls.ToolBar> um que usa um <xref:System.Windows.Media.LinearGradientBrush> horizontal para desenhar seu plano de fundo com um gradiente da esquerda para a direita.  

 ![Gráfico que mostra uma barra de ferramentas com um gradiente da esquerda para a direita.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 Depois de definir <xref:System.Windows.FlowDirection> como <xref:System.Windows.FlowDirection.RightToLeft>, não apenas os <xref:System.Windows.Controls.ToolBar> botões são organizados da direita para a esquerda, mas até <xref:System.Windows.Media.LinearGradientBrush> mesmo os realinham seus deslocamentos para fluir da direita para a esquerda.  
  
 O gráfico a seguir mostra o realinhamento do <xref:System.Windows.Media.LinearGradientBrush>.  
    
 ![Gráfico que mostra uma barra de ferramentas com um gradiente da direita para a esquerda.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 O exemplo a seguir desenha <xref:System.Windows.FlowDirection.RightToLeft>um <xref:System.Windows.Controls.ToolBar>. (Para desenhá-lo da esquerda para a direita <xref:System.Windows.FlowDirection> , remova o <xref:System.Windows.Controls.ToolBar>atributo no.  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Exceções de FlowDirection  
 Há alguns casos em que <xref:System.Windows.FlowDirection> o não se comporta conforme o esperado. Esta seção aborda duas dessas exceções.  
  
 **Image**  
  
 Um <xref:System.Windows.Controls.Image> representa um controle que exibe uma imagem. Ele pode ser usado com uma <xref:System.Windows.Controls.Image.Source%2A> propriedade <xref:System.Windows.Controls.Image> que define o [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] do a ser exibido. [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]  
  
 Ao contrário [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de outros elementos <xref:System.Windows.Controls.Image> , um não herda <xref:System.Windows.FlowDirection> o do contêiner. No entanto, <xref:System.Windows.FlowDirection> se o for definido <xref:System.Windows.FlowDirection.RightToLeft>explicitamente como <xref:System.Windows.Controls.Image> , um será exibido horizontalmente. Isso é implementado como um recurso conveniente para desenvolvedores de conteúdo bidirecional, pois, em alguns casos, inverter a imagem horizontalmente produz o efeito desejado.  
  
 O gráfico a seguir mostra uma invertida <xref:System.Windows.Controls.Image>.  
    
 ![Gráfico que ilustra uma imagem invertida.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 O exemplo a seguir demonstra que <xref:System.Windows.Controls.Image> o não herda o <xref:System.Windows.FlowDirection> do <xref:System.Windows.Controls.StackPanel> que o contém. **Observação** Você deve ter um arquivo chamado **ms_logo. jpg** em C:\ para executar este exemplo.  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Observação** Estão incluídos nos arquivos de download um arquivo **ms_logo. jpg** . O código pressupõe que o arquivo .jpg não está dentro do projeto, mas em algum lugar na unidade C:\. É necessário copiar o .jpg dos arquivos de projeto para a unidade C:\ ou alterar o código para procurar o arquivo dentro do projeto. Para fazer isso, `Source="file://c:/ms_logo.jpg"` Altere `Source="ms_logo.jpg"`para.  
  
 **Caminhos**  
  
 Além de um <xref:System.Windows.Controls.Image>, outro elemento interessante é <xref:System.Windows.Shapes.Path>. Um Caminho é um objeto que pode desenhar uma série de linhas e curvas conectadas. Ele se comporta de uma <xref:System.Windows.Controls.Image> maneira semelhante a uma sobre sua <xref:System.Windows.FlowDirection>; por exemplo, seu <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> é um espelho horizontal de seu <xref:System.Windows.FlowDirection.LeftToRight> . No entanto, <xref:System.Windows.Controls.Image>ao <xref:System.Windows.Shapes.Path> contrário de <xref:System.Windows.FlowDirection> um, herda seu do contêiner e um não precisa especificá-lo explicitamente.  
  
 O exemplo a seguir desenha uma seta simples usando 3 linhas. A primeira seta herda a <xref:System.Windows.FlowDirection.RightToLeft> direção do fluxo <xref:System.Windows.Controls.StackPanel> do para que seus pontos inicial e final sejam medidos de uma raiz no lado direito. A segunda seta que tem um explícito <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> também é iniciada no lado direito. No entanto, a terceira seta tem sua raiz inicial no lado esquerdo. Para obter mais informações sobre o <xref:System.Windows.Media.LineGeometry> desenho <xref:System.Windows.Media.GeometryGroup>, consulte e.  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 O gráfico a seguir mostra a saída do exemplo anterior com setas desenhadas `Path` usando o elemento:

 ![Gráfico que ilustra as setas desenhadas usando o elemento Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 O <xref:System.Windows.Controls.Image> e <xref:System.Windows.Shapes.Path> o são dois exemplos de como [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] o <xref:System.Windows.FlowDirection>usa. Ao lado de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dispor elementos em uma direção específica dentro de um <xref:System.Windows.FlowDirection> contêiner, pode ser <xref:System.Windows.Controls.InkPresenter> usado com elementos como, por exemplo, que renderiza a <xref:System.Windows.Media.LinearGradientBrush>tinta <xref:System.Windows.Media.RadialGradientBrush>em uma superfície,,. Sempre que você precisar de um comportamento da direita para a esquerda para seu conteúdo que imita um comportamento da esquerda para a direita, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ou vice-versa, ele fornece essa funcionalidade.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Substituição de números  
 Historicamente, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] o tem suporte para substituição de números, permitindo a representação de diferentes formas culturais para os mesmos dígitos, ao mesmo tempo em que mantém o armazenamento interno desses dígitos unificado entre diferentes localidades, por exemplo, os números são armazenados em seus valores hexadecimais bem conhecidos, 0x40, 0x41, mas são exibidos de acordo com o idioma selecionado.  
  
 Isso permitiu que os aplicativos processassem valores numéricos sem a necessidade de convertê-los de um idioma para outro, por exemplo, um [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] usuário pode abrir uma planilha [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] em um árabe localizado e ver os números moldados em árabe, mas abri-los em uma versão europeia do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e consulte representação Europeia dos mesmos números. Isso também é necessário para outros símbolos, como separadores de vírgula e símbolo de percentual, porque eles geralmente acompanham os números no mesmo documento.  
  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dá continuidade à mesma tradição e adiciona suporte adicional a esse recurso, o que permite maior controle do usuário sobre quando e como a substituição é usada. Embora esse recurso tenha sido projetado para qualquer idioma, ele é particularmente útil no conteúdo bidirecional, em que a formatação de dígitos de um idioma específico é, de modo geral, um desafio para os desenvolvedores de aplicativos, devido às várias culturas nas quais um aplicativo pode ser executado.  
  
 A propriedade Core que controla como o número de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] substituição funciona <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> é a propriedade de dependência. A <xref:System.Windows.Media.NumberSubstitution> classe especifica como os números no texto devem ser exibidos. Ela tem três propriedades públicas que definem seu comportamento. Veja a seguir um resumo de cada uma das propriedades.  
  
 **CultureSource:**  
  
 Essa propriedade especifica como a cultura para números é determinada. Ele usa um dos três <xref:System.Windows.Media.NumberCultureSource> valores de enumeração.  
  
- Substituição A cultura numérica é aquela <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> da propriedade.  
  
- Texto A cultura de número é a cultura da execução do texto. Em marcação `xml:lang`, isso seria ou sua propriedade de alias `Language` (<xref:System.Windows.FrameworkElement.Language%2A> ou <xref:System.Windows.FrameworkContentElement.Language%2A>). Além disso, é o padrão para classes derivadas de <xref:System.Windows.FrameworkContentElement>. Essas classes incluem <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType> <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, eassimpordiante.<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>  
  
- Usuário A cultura de número é a cultura do thread atual. Essa propriedade é o padrão para todas as subclasses <xref:System.Windows.FrameworkElement> de <xref:System.Windows.Controls.Page>como, <xref:System.Windows.Window> e <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 A <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriedade só será usada se a <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> propriedade for definida como <xref:System.Windows.Media.NumberCultureSource.Override> e for ignorada de outra forma. Ela especifica a cultura dos números. Um valor de `null`, o valor padrão, é interpretado como en-US.  
  
 **Substitution**:  
  
 Essa propriedade especifica o tipo de substituição de números a ser executado. Ele usa um dos seguintes <xref:System.Windows.Media.NumberSubstitutionMethod> valores de enumeração:  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: O método de substituição é determinado com base na propriedade da <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> cultura do número. Esse é o padrão.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Se a cultura do número for uma cultura árabe ou persa, ela especificará que os dígitos dependem do contexto.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Os números sempre são renderizados como dígitos europeus.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Os números são renderizados usando os dígitos nacionais para a cultura de número, conforme especificado pela <xref:System.Globalization.CultureInfo.NumberFormat%2A>cultura.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Os números são renderizados usando os dígitos tradicionais para a cultura de número. Para a maioria das culturas, isso é o <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>mesmo que. No entanto, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> resulta em dígitos latinos para algumas culturas árabes, enquanto esse valor resulta em dígitos árabes para todas as culturas árabes.  
  
 O que esses valores significam para um desenvolvedor de conteúdo bidirecional? Na maioria dos casos, o desenvolvedor pode precisar apenas definir <xref:System.Windows.FlowDirection> e o idioma de cada elemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] textual, por exemplo `Language="ar-SA"` , e <xref:System.Windows.Media.NumberSubstitution> a lógica cuida da exibição dos números de acordo com o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]correto. O exemplo a seguir demonstra o uso de números em árabe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e em inglês em um aplicativo em [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]execução em uma versão em árabe do.  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 O gráfico a seguir mostra a saída do exemplo anterior se você estiver executando em uma versão em árabe do Windows com os números árabe e inglês exibidos:

 ![Gráfico que mostra números em árabe e em inglês.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 O <xref:System.Windows.FlowDirection> era importante, nesse caso, porque a <xref:System.Windows.FlowDirection> definição <xref:System.Windows.FlowDirection.LeftToRight> de para, em vez disso, teria um resultado de dígitos europeus. As próximas seções abordam como ter uma exibição unificada de dígitos em todo o documento. Se esse exemplo não estiver sendo executado no Windows em árabe, todos os dígitos serão exibidos como dígitos europeus.  
  
 **Definindo regras de substituição**  
  
 Em um aplicativo real, talvez você deseje definir o Idioma de forma programática. Por exemplo, você deseja definir o `xml:lang` atributo como o mesmo usado pelo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]sistema, ou talvez alterar o idioma, dependendo do estado do aplicativo.  
  
 Se você quiser fazer alterações com base no estado do aplicativo, faça uso de outros recursos fornecidos pelo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Primeiro, defina o componente do `NumberSubstitution.CultureSource="Text"`aplicativo. Usar essa configuração garante que as configurações não venham do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para elementos de texto que tenham "user" como o padrão, <xref:System.Windows.Controls.TextBlock>como.  
  
Por exemplo:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

No código correspondente C# , defina a `Language` Propriedade, por exemplo, para `"ar-SA"`.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Se você precisar definir a `Language` propriedade para o idioma da interface do usuário atual, use o código a seguir.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>representa a cultura atual usada pelo thread atual em tempo de execução.  
  
 O exemplo [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] final deve ser semelhante ao exemplo a seguir.  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 O exemplo C# final deve ser semelhante ao seguinte.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 O gráfico a seguir mostra a aparência da janela para a linguagem de programação, exibindo números árabes:
     
 ![Gráfico que exibe os números árabes.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **Usando a propriedade de substituição**  
  
 O modo pelo qual a substituição [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de número funciona depende do idioma do elemento de texto e <xref:System.Windows.FlowDirection>de seu. Se o <xref:System.Windows.FlowDirection> for da esquerda para a direita, os dígitos europeus serão renderizados. No entanto, se ele for precedido por texto em árabe ou tiver o idioma definido como "ar <xref:System.Windows.FlowDirection> " <xref:System.Windows.FlowDirection.RightToLeft>e o for, os dígitos árabes serão renderizados em vez disso.  
  
 No entanto, em alguns casos, talvez você deseje criar um aplicativo unificado, por exemplo, europeus dígitos para todos os usuários. Ou dígitos árabes em <xref:System.Windows.Documents.Table> células com um específico <xref:System.Windows.Style>. Uma maneira fácil de fazer isso é usando a <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade.  
  
 No exemplo a seguir, o primeiro <xref:System.Windows.Controls.TextBlock> não tem a <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade definida, portanto, o algoritmo exibe os dígitos árabes conforme o esperado. No entanto, <xref:System.Windows.Controls.TextBlock>na segunda, a substituição é definida como European substituindo a substituição padrão por números árabes e os dígitos europeus são exibidos.  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
