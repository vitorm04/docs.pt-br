---
title: "Visão geral dos recursos bidirecionais no WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b50d98d5f02a59a013d7577f0e312e6ffde35690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bidirectional-features-in-wpf-overview"></a>Visão geral dos recursos bidirecionais no WPF
Ao contrário de qualquer outra plataforma de desenvolvimento, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem muitos recursos que dão suporte ao desenvolvimento rápido de conteúdo bidirecional, por exemplo, mista esquerda para a direita e direita para esquerda dados no mesmo documento. Ao mesmo tempo, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria uma excelente experiência para usuários que necessitam de recursos bidirecionais, como árabe e hebraico falando de usuários.  
  
 As próximas seções explicam vários recursos bidirecionais junto com exemplos que ilustram como obter a melhor exibição do conteúdo bidirecional. A maioria dos exemplos usa [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], embora você pode aplicar facilmente os conceitos para [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] ou [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] código.  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 A propriedade básica que define a direção do fluxo de conteúdo em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo é <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Essa propriedade pode ser definida como um dos dois valores de enumeração, <xref:System.Windows.FlowDirection.LeftToRight> ou <xref:System.Windows.FlowDirection.RightToLeft>. A propriedade está disponível para todos os [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos que herdam de <xref:System.Windows.FrameworkElement>.  
  
 Os exemplos a seguir definem a direção do fluxo de um <xref:System.Windows.Controls.TextBox> elemento.  
  
 **Direção do fluxo da esquerda para a direita**  
  
 [!code-xaml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Direção do fluxo da direita para a esquerda**  
  
 [!code-xaml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 O gráfico a seguir mostra como o código anterior é renderizado.  
  
 **Gráfico que ilustra a FlowDirection**  
  
 ![Alinhamento do TextBlock](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 Um elemento dentro de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] árvore herdará o <xref:System.Windows.FrameworkElement.FlowDirection%2A> de seu contêiner. No exemplo a seguir, o <xref:System.Windows.Controls.TextBlock> está dentro de um <xref:System.Windows.Controls.Grid>, que reside em um <xref:System.Windows.Window>. Definindo o <xref:System.Windows.FrameworkElement.FlowDirection%2A> para o <xref:System.Windows.Window> implica configurá-la para o <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Controls.TextBlock> também.  
  
 O exemplo a seguir mostra a configuração <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 O nível superior <xref:System.Windows.Window> tem um <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, portanto, todos os elementos contidos nele também herdam o mesmo <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Para um elemento substituir um especificado <xref:System.Windows.FrameworkElement.FlowDirection%2A> ele deve adicionar uma alteração de direção explícito, como a segunda <xref:System.Windows.Controls.TextBlock> no exemplo anterior que altera para <xref:System.Windows.FlowDirection.LeftToRight>. Quando nenhum <xref:System.Windows.FrameworkElement.FlowDirection%2A> for definida, o padrão <xref:System.Windows.FlowDirection.LeftToRight> se aplica.  
  
 O gráfico a seguir mostra o resultado do exemplo anterior.  
  
 **Gráfico que ilustra a FlowDirection atribuída explicitamente**  
  
 ![Ilustração da direção do fluxo](../../../../docs/framework/wpf/advanced/media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Muitas plataformas de desenvolvimento, como [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e Java fornece suporte especial para o desenvolvimento de conteúdo bidirecional. Linguagens de marcação como [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dar criadores de conteúdo a marcação necessário para exibir o texto em qualquer direção necessária, por exemplo o [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 marca, "dir" que usa "rtl" ou "ltr" como valores. Essa marca é semelhante do <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade, mas o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade funciona de maneira mais avançada para o conteúdo textual do layout e pode ser usada para o conteúdo que não sejam de texto.  
  
 Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], um <xref:System.Windows.Documents.FlowDocument> é um versátil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento que pode hospedar uma combinação de texto, tabelas, imagens e outros elementos. As amostras das próximas seções usam esse elemento.  
  
 Adicionar texto a um <xref:System.Windows.Documents.FlowDocument> pode ser feito de mais que uma forma. É uma maneira simples de fazer isso por meio de um <xref:System.Windows.Documents.Paragraph> que é um elemento de nível de bloco usado para agrupar o conteúdo, como texto. Para adicionar texto ao usam os exemplos de elementos de nível incorporado <xref:System.Windows.Documents.Span> e <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span>é um elemento de conteúdo de nível interno usado para agrupar outros elementos embutidos, enquanto um <xref:System.Windows.Documents.Run> é um fluxo de nível embutido conteúdo de elemento deve conter uma execução de texto sem formatação. Um <xref:System.Windows.Documents.Span> pode conter vários <xref:System.Windows.Documents.Run> elementos.  
  
 O primeiro exemplo de documento contém um documento que tem um número de rede a compartilhar nomes; Por exemplo `\\server1\folder\file.ext`. Se você tiver esse link de rede em um documento em árabe ou em inglês, você sempre desejará que ele seja exibido da mesma maneira. O gráfico a seguir mostra o link em um árabe <xref:System.Windows.FlowDirection.RightToLeft> documento.  
  
 **Gráfico que ilustra o uso do elemento de extensão**  
  
 ![Documento que flui da direita para a esquerda](../../../../docs/framework/wpf/advanced/media/flowdocument.PNG "FlowDocument")  
  
 Como o texto é <xref:System.Windows.FlowDirection.RightToLeft>especial todos os caracteres, como o "\\", separar o texto em uma ordem da direita para esquerda. O resultado é o link não seja mostrado na ordem correta, portanto, para solucionar o problema, o texto deve ser incorporado para preservar um separado <xref:System.Windows.Documents.Run> fluindo <xref:System.Windows.FlowDirection.LeftToRight>. Em vez de ter um separado <xref:System.Windows.Documents.Run> para cada idioma, uma melhor maneira de resolver o problema é inserir o texto em inglês com menos frequência usado em uma maior árabe <xref:System.Windows.Documents.Span>.  
  
 O gráfico a seguir ilustra isso.  
  
 **Gráfico que ilustra o uso do elemento de sequência inserido em um elemento de extensão**  
  
 ![Captura de tela de XamlPad](../../../../docs/framework/wpf/advanced/media/runspan.PNG "RunSpan")  
  
 O exemplo a seguir demonstra o uso de <xref:System.Windows.Documents.Run> e <xref:System.Windows.Documents.Span> elementos em documentos.  
  
 [!code-xaml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Elementos de extensão  
 O <xref:System.Windows.Documents.Span> elemento funciona como um separador de limite entre textos com instruções de fluxo diferente.  Até mesmo <xref:System.Windows.Documents.Span> elementos com a mesma direção de fluxo são considerados como tendo escopos diferentes bidirecional, que significa que o <xref:System.Windows.Documents.Span> elementos são ordenados no contêiner de <xref:System.Windows.FlowDirection>, somente o conteúdo dentro do <xref:System.Windows.Documents.Span> elemento segue o <xref:System.Windows.FlowDirection> do <xref:System.Windows.Documents.Span>.  
  
 O gráfico a seguir mostra a direção do fluxo de várias <xref:System.Windows.Controls.TextBlock> elementos.  
  
 **Gráfico que ilustra a FlowDirection em vários elementos TextBlock**  
  
 ![Blocos de texto com direções de fluxo diferentes](../../../../docs/framework/wpf/advanced/media/span.PNG "Span")  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Documents.Span> e <xref:System.Windows.Documents.Run> elementos para produzir os resultados mostrados no gráfico anterior.  
  
 [!code-xaml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 No <xref:System.Windows.Controls.TextBlock> elementos no exemplo, o <xref:System.Windows.Documents.Span> elementos são dispostos acordo com o <xref:System.Windows.FlowDirection> de seus pais, mas o texto dentro de cada <xref:System.Windows.Documents.Span> fluxos de elemento de acordo com seu próprio <xref:System.Windows.FlowDirection>. Isso é aplicável ao latim e ao árabe – ou a qualquer outro idioma.  
  
### <a name="adding-xmllang"></a>Adicionando xml:lang  
 O gráfico a seguir mostra outro exemplo que usa números e expressões aritméticas, como `"200.0+21.4=221.4"`. Observe que apenas o <xref:System.Windows.FlowDirection> está definido.  
  
 **Gráfico que exibe números usando apenas a FlowDirection**  
  
 ![Números que fluem da direita para a esquerda](../../../../docs/framework/wpf/advanced/media/langattribute.PNG "LangAttribute")  
  
 Os usuários desse aplicativo serão ser decepcionada com o fato pela saída, mesmo que o <xref:System.Windows.FlowDirection> está correta, os números não são formatados como números arábicos devem ser formatados.  
  
 Elementos XAML podem incluir um [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atributo (`xml:lang`) que define o idioma de cada elemento. XAML também oferece suporte a um [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] princípio de idioma no qual `xml:lang` aplicados aos elementos pai na árvore de valores são usados por elementos filho. No exemplo anterior, porque um idioma não foi definido para o <xref:System.Windows.Documents.Run> elementos, o padrão de nível de elemento ou qualquer um de seus principais `xml:lang` foi usado, que é `en-US` para XAML. O algoritmo de formatação numérico interno de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] números seleciona o idioma correspondente – nesse caso é em inglês. Para tornar o árabe números renderizam corretamente `xml:lang` deve ser definido.  
  
 O gráfico a seguir mostra o exemplo com `xml:lang` adicionado.  
  
 **Gráfico que ilustra o uso do atributo xml:lang**  
  
 ![Números em árabe que fluem da direita para a esquerda](../../../../docs/framework/wpf/advanced/media/langattribute2.PNG "LangAttribute2")  
  
 O exemplo a seguir adiciona `xml:lang` ao aplicativo.  
  
 [!code-xaml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Lembre-se de que muitos idiomas têm diferentes `xml:lang` valores de acordo com a região de destino, por exemplo, `"ar-SA"` e `"ar-EG"` representar duas variações árabe. Os exemplos anteriores ilustram que você precisa definir ambos os `xml:lang` e <xref:System.Windows.FlowDirection> valores.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection com elementos não texto  
 <xref:System.Windows.FlowDirection>Define não apenas como texto flui em um elemento de texto, mas também a direção do fluxo de quase todos os outros [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento. A gráfico a seguir mostra um <xref:System.Windows.Controls.ToolBar> que usa um horizontal <xref:System.Windows.Media.LinearGradientBrush> para desenhar o plano de fundo.  
  
 **Gráfico que mostra uma barra de ferramentas com um gradiente da esquerda para a direita**  
  
 ![Captura de tela do gradiente](../../../../docs/framework/wpf/advanced/media/gradient.PNG "Gradient")  
  
 Depois de definir o <xref:System.Windows.FlowDirection> para <xref:System.Windows.FlowDirection.RightToLeft>, não apenas o <xref:System.Windows.Controls.ToolBar> botões são organizados da direita para a esquerda, mas até mesmo o <xref:System.Windows.Media.LinearGradientBrush> realigns seus deslocamentos para fluir da direita para a esquerda.  
  
 O gráfico a seguir mostra o realinhamento do <xref:System.Windows.Media.LinearGradientBrush>.  
  
 **Gráfico que mostra uma barra de ferramentas com um gradiente da direita para a esquerda**  
  
 ![Um gradiente que flui da direita para a esquerda](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 O exemplo a seguir desenha um <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Para desenhar esquerda para direita, remover o <xref:System.Windows.FlowDirection> atributo no <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Exceções de FlowDirection  
 Há alguns casos onde <xref:System.Windows.FlowDirection> não se comportar conforme o esperado. Esta seção aborda duas dessas exceções.  
  
 **Image**  
  
 Um <xref:System.Windows.Controls.Image> representa um controle que exibe uma imagem. Em [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pode ser usado com um <xref:System.Windows.Controls.Image.Source%2A> propriedade que define o [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] do <xref:System.Windows.Controls.Image> para exibir.  
  
 Ao contrário de outras [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos, um <xref:System.Windows.Controls.Image> não herda de <xref:System.Windows.FlowDirection> do contêiner. No entanto, se o <xref:System.Windows.FlowDirection> é definido explicitamente como <xref:System.Windows.FlowDirection.RightToLeft>, uma <xref:System.Windows.Controls.Image> é exibido invertido horizontalmente. Isso é implementado como um recurso conveniente para desenvolvedores de conteúdo bidirecional, pois, em alguns casos, inverter a imagem horizontalmente produz o efeito desejado.  
  
 O gráfico a seguir mostra um invertidos <xref:System.Windows.Controls.Image>.  
  
 **Gráfico que ilustra uma imagem invertida**  
  
 ![Captura de tela de XamlPad](../../../../docs/framework/wpf/advanced/media/image.PNG "Image")  
  
 O exemplo a seguir demonstra que o <xref:System.Windows.Controls.Image> não herdam a <xref:System.Windows.FlowDirection> do <xref:System.Windows.Controls.StackPanel> que o contém. **Observação** deve ter um arquivo chamado **ms_logo.jpg** na unidade C:\ para executar este exemplo.  
  
 [!code-xaml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Observação** incluídos nos arquivos de download é um **ms_logo.jpg** arquivo. O código pressupõe que o arquivo .jpg não está dentro do projeto, mas em algum lugar na unidade C:\. É necessário copiar o .jpg dos arquivos de projeto para a unidade C:\ ou alterar o código para procurar o arquivo dentro do projeto. Para fazer essa alteração `Source="file://c:/ms_logo.jpg"` para `Source="ms_logo.jpg"`.  
  
 **Caminhos**  
  
 Além de um <xref:System.Windows.Controls.Image>, outro elemento interessante é <xref:System.Windows.Shapes.Path>. Um Caminho é um objeto que pode desenhar uma série de linhas e curvas conectadas. Se comporta de forma semelhante a um <xref:System.Windows.Controls.Image> em relação ao seu <xref:System.Windows.FlowDirection>; por exemplo seu <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> é um espelho horizontal do seu <xref:System.Windows.FlowDirection.LeftToRight> um. No entanto, ao contrário de um <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> herda seu <xref:System.Windows.FlowDirection> do contêiner e um não precisa especificá-lo explicitamente.  
  
 O exemplo a seguir desenha uma seta simples usando 3 linhas. A primeira seta herda o <xref:System.Windows.FlowDirection.RightToLeft> direção de fluxo do <xref:System.Windows.Controls.StackPanel> para que seus pontos inicial e final são medidos de uma raiz no lado direito. A segunda seta que tem uma explícita <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> também inicia no lado direito. No entanto, a terceira seta tem sua raiz inicial no lado esquerdo. Para obter mais informações sobre como desenhar consulte <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 O gráfico a seguir mostra o resultado do exemplo anterior.  
  
 **Gráfico que ilustra setas desenhadas com o elemento de caminho**  
  
 ![Caminhos](../../../../docs/framework/wpf/advanced/media/paths.PNG "Paths")  
  
 O <xref:System.Windows.Controls.Image> e <xref:System.Windows.Shapes.Path> são dois exemplos de um como [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] usa <xref:System.Windows.FlowDirection>. Ao lado de dispor [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos em uma direção específica dentro de um contêiner, <xref:System.Windows.FlowDirection> pode ser usado com elementos como <xref:System.Windows.Controls.InkPresenter> que renderiza a tinta em uma superfície <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Sempre que você precisa de um direito de comportamento esquerdo para o conteúdo que simule uma esquerda para direita comportamento, ou vice-versa, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece esse recurso.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Substituição de números  
 Historicamente, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] tem suporte para a substituição de número, permitindo que a representação de diferentes formas culturais para os dígitos mesmo mantendo o armazenamento interno desses dígitos unificada entre localidades diferentes, para números de exemplo são armazenados no os conhecidos valores hexadecimais, 0x40, 0x41, mas exibidos de acordo com o idioma selecionado.  
  
 Isso permitiu aplicativos processar valores numéricos sem a necessidade de convertê-los de um idioma para outro, por exemplo, um usuário pode abrir um [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] planilha em uma árabe [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e ver os números formatados em árabe, mas abri-lo no uma versão europeu de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e consulte representação Europeu dos mesmos números. Isso também é necessário para outros símbolos, como separadores de vírgula e símbolo de percentual, porque eles geralmente acompanham os números no mesmo documento.  
  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dá continuidade à mesma tradição e adiciona suporte adicional a esse recurso, o que permite maior controle do usuário sobre quando e como a substituição é usada. Embora esse recurso tenha sido projetado para qualquer idioma, ele é particularmente útil no conteúdo bidirecional, em que a formatação de dígitos de um idioma específico é, de modo geral, um desafio para os desenvolvedores de aplicativos, devido às várias culturas nas quais um aplicativo pode ser executado.  
  
 A propriedade de núcleo controlando a substituição de número como funciona em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é o <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade de dependência. O <xref:System.Windows.Media.NumberSubstitution> classe especifica como números em texto a ser exibido. Ela tem três propriedades públicas que definem seu comportamento. Veja a seguir um resumo de cada uma das propriedades.  
  
 **CultureSource:**  
  
 Essa propriedade especifica como a cultura para números é determinada. Ele usa um dos três <xref:System.Windows.Media.NumberCultureSource> valores de enumeração.  
  
-   Substituir: Cultura número é de <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriedade.  
  
-   Texto: a cultura dos números é a cultura da sequência de texto. Na marcação, isso deveria ser `xml:lang`, ou seu alias `Language` propriedade (<xref:System.Windows.FrameworkElement.Language%2A> ou <xref:System.Windows.FrameworkContentElement.Language%2A>). Além disso, ele é o padrão para classes derivadas de <xref:System.Windows.FrameworkContentElement>. Essas classes incluem <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> e assim por diante.  
  
-   Usuário: a cultura dos números é a cultura do thread atual. Essa propriedade é o padrão para todas as subclasses de <xref:System.Windows.FrameworkElement> como <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> e <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 O <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriedade é usada somente se o <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> está definida como <xref:System.Windows.Media.NumberCultureSource.Override> e será ignorada caso contrário. Ela especifica a cultura dos números. Um valor de `null`, o valor padrão é interpretado como en-US.  
  
 **Substitution**:  
  
 Essa propriedade especifica o tipo de substituição de números a ser executado. Ele usa um dos seguintes <xref:System.Windows.Media.NumberSubstitutionMethod> valores de enumeração.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: O método de substituição é determinado com base na cultura do número do <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> propriedade. Esse é o padrão.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Se a cultura de número é uma cultura árabe ou Farsi, especifica que os dígitos dependem do contexto.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Números sempre são renderizados como dígitos europeus.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Números renderizados usando os dígitos nacionais para a cultura de número, conforme especificado pela cultura <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Números são renderizados usando os dígitos tradicionais para a cultura de número. Na maioria das culturas, isso é o mesmo que <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. No entanto, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> resulta em latinos dígitos para algumas culturas árabes, enquanto esse valor resulta em árabes dígitos para todas as culturas árabes.  
  
 O que esses valores significam para um desenvolvedor de conteúdo bidirecional? Na maioria dos casos, o desenvolvedor pode precisar apenas definir <xref:System.Windows.FlowDirection> e o idioma de cada textual [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento, por exemplo `Language="ar-SA"` e <xref:System.Windows.Media.NumberSubstitution> lógica se encarrega de exibir os números de acordo com o correto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O exemplo a seguir demonstra o uso de números em árabe e inglês em um [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativo executado em uma versão em árabe do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 O gráfico a seguir mostra a saída do exemplo anterior, se você estiver executando uma versão árabe do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 **Gráfico que mostra os números em árabe e inglês exibidos**  
  
 ![Captura de tela de XamlPad com números](../../../../docs/framework/wpf/advanced/media/numbers.PNG "Numbers")  
  
 O <xref:System.Windows.FlowDirection> era importante nesse caso, como definir o <xref:System.Windows.FlowDirection> para <xref:System.Windows.FlowDirection.LeftToRight> em vez disso seria produziram dígitos europeus. As próximas seções abordam como ter uma exibição unificada de dígitos em todo o documento. Se esse exemplo não estiver sendo executado no Windows em árabe, todos os dígitos serão exibidos como dígitos europeus.  
  
 **Definindo regras de substituição**  
  
 Em um aplicativo real, talvez você deseje definir o Idioma de forma programática. Por exemplo, você deseja definir o `xml:lang` atributo para ser o mesmo que aquele usado pelo sistema de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ou talvez alterar o idioma dependendo do estado do aplicativo.  
  
 Se você quiser fazer alterações com base no estado do aplicativo, verifique o uso de outros recursos fornecidos pelo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Primeiro, defina o componente de aplicativo `NumberSubstitution.CultureSource="Text"`. Usar essa configuração garante que as configurações não sejam provenientes do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para elementos de texto que contêm "Usuário" como o padrão, como <xref:System.Windows.Controls.TextBlock>.  
  
 Por exemplo:  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 No correspondente [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] de código, defina o `Language` propriedade, por exemplo, para `"ar-SA"`.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 Se você precisar definir o `Language` propriedade para o usuário atual [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] idioma usar o código a seguir.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A>representa a cultura atual usada pelo thread atual em tempo de execução.  
  
 O final [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] exemplo deve ser semelhante ao exemplo a seguir.  
  
 [!code-xaml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 O final [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] exemplo deve ser semelhante à seguinte.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 O gráfico a seguir mostra a aparência de janela em qualquer linguagem de programação.  
  
 **Gráfico que exibe números em árabe**  
  
 ![Números em árabe](../../../../docs/framework/wpf/advanced/media/numbers2.PNG "Numbers2")  
  
 **Usando a propriedade de substituição**  
  
 A substituição de maneira número funciona em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] depende no idioma do elemento de texto e seu <xref:System.Windows.FlowDirection>. Se o <xref:System.Windows.FlowDirection> é da esquerda para direita, em seguida, os dígitos europeus são renderizados. No entanto se ele é precedido por texto em árabe, ou o idioma definido como "ar" e o <xref:System.Windows.FlowDirection> é <xref:System.Windows.FlowDirection.RightToLeft>, árabes dígitos são renderizados em vez disso.  
  
 No entanto, em alguns casos, talvez você deseje criar um aplicativo unificado, por exemplo, europeus dígitos para todos os usuários. Ou árabes dígitos no <xref:System.Windows.Documents.Table> células com um determinado <xref:System.Windows.Style>. Uma maneira fácil de fazer o que está usando o <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade.  
  
 No exemplo a seguir, a primeira <xref:System.Windows.Controls.TextBlock> não tem o <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriedade definida para o algoritmo exibe dígitos árabes conforme o esperado. No entanto no segundo <xref:System.Windows.Controls.TextBlock>, a substituição está definida para Europeu substituindo a substituição padrão para números arábicos e os dígitos europeus são exibidos.  
  
 [!code-xaml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
