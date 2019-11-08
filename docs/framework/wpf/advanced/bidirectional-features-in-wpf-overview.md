---
title: Visão geral dos recursos bidirecionais no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 385ce8d263991361512371dcacff52fcf0bbe738
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740940"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Visão geral dos recursos bidirecionais no WPF

Ao contrário de qualquer outra plataforma de desenvolvimento, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem muitos recursos que dão suporte ao desenvolvimento rápido de conteúdo bidirecional, por exemplo, misto da esquerda para a direita e da direita para a esquerda nos dados no mesmo documento. Ao mesmo tempo, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria uma experiência excelente para os usuários que precisam de recursos bidirecionais, como o árabe e o Hebraico falando com os usuários.

As próximas seções explicam vários recursos bidirecionais junto com exemplos que ilustram como obter a melhor exibição do conteúdo bidirecional. A maioria dos exemplos usa XAML, embora você possa facilmente aplicar os conceitos ao C# ou ao Microsoft Visual Basic Code.

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

A propriedade básica que define a direção do fluxo de conteúdo em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Essa propriedade pode ser definida como um dos dois valores de enumeração, <xref:System.Windows.FlowDirection.LeftToRight> ou <xref:System.Windows.FlowDirection.RightToLeft>. A propriedade está disponível para todos os elementos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que herdam de <xref:System.Windows.FrameworkElement>.

Os exemplos a seguir definem a direção do fluxo de um elemento <xref:System.Windows.Controls.TextBox>.

**Direção do fluxo da esquerda para a direita**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**Direção do fluxo da direita para a esquerda**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

O gráfico a seguir mostra como o código anterior é renderizado.

![Gráfico que ilustra as diferentes direções de fluxo.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

Um elemento dentro de uma árvore de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] herdará o <xref:System.Windows.FrameworkElement.FlowDirection%2A> de seu contêiner. No exemplo a seguir, o <xref:System.Windows.Controls.TextBlock> está dentro de um <xref:System.Windows.Controls.Grid>, que reside em uma <xref:System.Windows.Window>. Definir o <xref:System.Windows.FrameworkElement.FlowDirection%2A> para o <xref:System.Windows.Window> implica defini-lo para o <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Controls.TextBlock> também.

O exemplo a seguir demonstra a configuração <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

O <xref:System.Windows.Window> de nível superior tem uma <xref:System.Windows.FlowDirection><xref:System.Windows.FlowDirection.RightToLeft>, portanto, todos os elementos contidos nela também herdam o mesmo <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Para um elemento substituir um <xref:System.Windows.FrameworkElement.FlowDirection%2A> especificado, ele deve adicionar uma alteração de direção explícita, como a segunda <xref:System.Windows.Controls.TextBlock> no exemplo anterior, que muda para <xref:System.Windows.FlowDirection.LeftToRight>. Quando nenhum <xref:System.Windows.FrameworkElement.FlowDirection%2A> é definido, o <xref:System.Windows.FlowDirection.LeftToRight> padrão se aplica.

O gráfico a seguir mostra a saída do exemplo anterior:

![Gráfico que ilustra a alteração da direção do fluxo explícito.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

Muitas plataformas de desenvolvimento, como HTML, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e Java, fornecem suporte especial para o desenvolvimento de conteúdo bidirecional. As linguagens de marcação, como HTML, dão aos gravadores de conteúdo a marcação necessária para exibir texto em qualquer direção necessária, por exemplo, a marca HTML 4,0, "dir" que usa "RTL" ou "EPD" como valores. Essa marca é semelhante à propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A>, mas a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> funciona de forma mais avançada para layout de conteúdo textual e pode ser usada para conteúdo que não seja texto.

No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], uma <xref:System.Windows.Documents.FlowDocument> é um elemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] versátil que pode hospedar uma combinação de texto, tabelas, imagens e outros elementos. As amostras das próximas seções usam esse elemento.

A adição de texto a uma <xref:System.Windows.Documents.FlowDocument> pode ser feita de uma maneira mais unidirecional. Uma maneira simples de fazer isso é por meio de um <xref:System.Windows.Documents.Paragraph> que é um elemento de nível de bloco usado para agrupar conteúdo, como texto. Para adicionar texto a elementos de nível embutido, as amostras usam <xref:System.Windows.Documents.Span> e <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> é um elemento de conteúdo de fluxo de nível embutido usado para agrupar outros elementos embutidos, enquanto uma <xref:System.Windows.Documents.Run> é um elemento de conteúdo de fluxo de nível embutido que deve conter uma execução de texto não formatado. Um <xref:System.Windows.Documents.Span> pode conter vários elementos <xref:System.Windows.Documents.Run>.

O primeiro exemplo de documento contém um documento que tem um número de nomes de compartilhamento de rede; por exemplo `\\server1\folder\file.ext`. Se você tiver esse link de rede em um documento em árabe ou em inglês, você sempre desejará que ele seja exibido da mesma maneira. O gráfico a seguir ilustra o uso do elemento span e mostra o link em um documento <xref:System.Windows.FlowDirection.RightToLeft> árabe:

![Gráfico que ilustra o uso do elemento span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

Como o texto é <xref:System.Windows.FlowDirection.RightToLeft>, todos os caracteres especiais, como "\\", separam o texto em uma ordem direita para a esquerda. Isso faz com que o link não seja mostrado na ordem correta, portanto, para resolver o problema, o texto deve ser inserido para preservar um <xref:System.Windows.FlowDirection.LeftToRight> de fluxo de <xref:System.Windows.Documents.Run> separado. Em vez de ter um <xref:System.Windows.Documents.Run> separado para cada idioma, uma maneira melhor de resolver o problema é inserir o texto em inglês com menos frequência em um <xref:System.Windows.Documents.Span> árabe maior.

O gráfico a seguir ilustra isso usando o elemento Run inserido em um elemento span:

![Gráfico que ilustra o elemento Run inserido em um elemento span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

O exemplo a seguir demonstra como usar <xref:System.Windows.Documents.Run> e <xref:System.Windows.Documents.Span> elementos em documentos.

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Elementos de extensão

O elemento <xref:System.Windows.Documents.Span> funciona como um separador de limite entre textos com direções de fluxo diferentes.  Até mesmo elementos <xref:System.Windows.Documents.Span> com a mesma direção de fluxo são considerados com escopos bidirecionais diferentes, o que significa que os elementos de <xref:System.Windows.Documents.Span> são ordenados na <xref:System.Windows.FlowDirection> do contêiner, somente o conteúdo dentro do elemento <xref:System.Windows.Documents.Span> segue a <xref:System.Windows.FlowDirection> do @no__ t_5.

O gráfico a seguir mostra a direção do fluxo de vários elementos <xref:System.Windows.Controls.TextBlock>.

![Gráfico que ilustra os blocos de texto com direções de fluxo diferentes.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

O exemplo a seguir mostra como usar os elementos <xref:System.Windows.Documents.Span> e <xref:System.Windows.Documents.Run> para produzir os resultados mostrados no gráfico anterior.

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

Nos elementos de <xref:System.Windows.Controls.TextBlock> no exemplo, os elementos de <xref:System.Windows.Documents.Span> são dispostos de acordo com o <xref:System.Windows.FlowDirection> de seus pais, mas o texto dentro de cada elemento de <xref:System.Windows.Documents.Span> flui de acordo com seu próprio <xref:System.Windows.FlowDirection>. Isso é aplicável ao latim e ao árabe – ou a qualquer outro idioma.

### <a name="adding-xmllang"></a>Adicionando xml:lang

O gráfico a seguir mostra outro exemplo que usa números e expressões aritméticas, como `"200.0+21.4=221.4"`. Observe que apenas o <xref:System.Windows.FlowDirection> está definido.

![Gráfico que exibe números usando apenas FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

Os usuários desse aplicativo serão desapontados pela saída, mesmo que o <xref:System.Windows.FlowDirection> esteja correto, os números não serão formatados como números árabes.

Os elementos XAML podem incluir um atributo XML (`xml:lang`) que define o idioma de cada elemento. O XAML também dá suporte a um princípio de linguagem XML no qual `xml:lang` valores aplicados aos elementos pai na árvore são usados por elementos filho. No exemplo anterior, como um idioma não foi definido para o elemento <xref:System.Windows.Documents.Run> ou qualquer um de seus elementos de nível superior, o `xml:lang` padrão foi usado, que é `en-US` para XAML. O algoritmo de formatação de número interno de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] seleciona números no idioma correspondente – neste caso, inglês. Para fazer com que os números árabes sejam processados corretamente `xml:lang` precisa ser definido.

O gráfico a seguir mostra o exemplo com `xml:lang` adicionado.

![Gráfico que ilustra os números árabes que fluem da direita para a esquerda.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

O exemplo a seguir adiciona `xml:lang` ao aplicativo.

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

Lembre-se de que muitas linguagens têm valores `xml:lang` diferentes, dependendo da região de destino, por exemplo, `"ar-SA"` e `"ar-EG"` representam duas variações de árabe. Os exemplos anteriores ilustram que você precisa definir os valores de `xml:lang` e de <xref:System.Windows.FlowDirection>.

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>FlowDirection com elementos não texto

<xref:System.Windows.FlowDirection> define não apenas como o texto flui em um elemento textual, mas também a direção do fluxo de quase todos os outros elementos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O gráfico a seguir mostra um <xref:System.Windows.Controls.ToolBar> que usa uma <xref:System.Windows.Media.LinearGradientBrush> horizontal para desenhar seu plano de fundo com um gradiente da esquerda para a direita.

![Gráfico que mostra uma barra de ferramentas com um gradiente da esquerda para a direita.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

Depois de definir o <xref:System.Windows.FlowDirection> como <xref:System.Windows.FlowDirection.RightToLeft>, não apenas os botões de <xref:System.Windows.Controls.ToolBar> são organizados da direita para a esquerda, mas até mesmo a <xref:System.Windows.Media.LinearGradientBrush> realinha seus deslocamentos para fluir da direita para a esquerda.

O gráfico a seguir mostra o realinhamento do <xref:System.Windows.Media.LinearGradientBrush>.

![Gráfico que mostra uma barra de ferramentas com um gradiente da direita para a esquerda.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

O exemplo a seguir desenha um <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Para desenhá-lo da esquerda para a direita, remova o atributo <xref:System.Windows.FlowDirection> no <xref:System.Windows.Controls.ToolBar>.

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>Exceções de FlowDirection

Há alguns casos em que <xref:System.Windows.FlowDirection> não se comporta conforme o esperado. Esta seção aborda duas dessas exceções.

**Image**

Um <xref:System.Windows.Controls.Image> representa um controle que exibe uma imagem. Em XAML, ele pode ser usado com uma propriedade <xref:System.Windows.Controls.Image.Source%2A> que define o URI (Uniform Resource Identifier) do <xref:System.Windows.Controls.Image> a ser exibido.

Ao contrário de outros elementos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], um <xref:System.Windows.Controls.Image> não herda o <xref:System.Windows.FlowDirection> do contêiner. No entanto, se o <xref:System.Windows.FlowDirection> for definido explicitamente para <xref:System.Windows.FlowDirection.RightToLeft>, um <xref:System.Windows.Controls.Image> será exibido horizontalmente. Isso é implementado como um recurso conveniente para desenvolvedores de conteúdo bidirecional, pois, em alguns casos, inverter a imagem horizontalmente produz o efeito desejado.

O gráfico a seguir mostra um <xref:System.Windows.Controls.Image> invertido.

![Gráfico que ilustra uma imagem invertida.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

O exemplo a seguir demonstra que o <xref:System.Windows.Controls.Image> falha ao herdar o <xref:System.Windows.FlowDirection> do <xref:System.Windows.Controls.StackPanel> que o contém.

> [!NOTE]
> Você deve ter um arquivo chamado **ms_logo. jpg** em C:\ para executar este exemplo.

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> Estão incluídos nos arquivos de download um arquivo **ms_logo. jpg** . O código pressupõe que o arquivo .jpg não está dentro do projeto, mas em algum lugar na unidade C:\. É necessário copiar o .jpg dos arquivos de projeto para a unidade C:\ ou alterar o código para procurar o arquivo dentro do projeto. Para fazer essa alteração `Source="file://c:/ms_logo.jpg"` `Source="ms_logo.jpg"`.

**Caminhos**

Além de um <xref:System.Windows.Controls.Image>, outro elemento interessante é <xref:System.Windows.Shapes.Path>. Um Caminho é um objeto que pode desenhar uma série de linhas e curvas conectadas. Ele se comporta de maneira semelhante a uma <xref:System.Windows.Controls.Image> sobre seu <xref:System.Windows.FlowDirection>; por exemplo, seu <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> é um espelho horizontal de seu <xref:System.Windows.FlowDirection.LeftToRight> um. No entanto, ao contrário de uma <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> herda sua <xref:System.Windows.FlowDirection> do contêiner e uma não precisa especificá-la explicitamente.

O exemplo a seguir desenha uma seta simples usando 3 linhas. A primeira seta herda a direção do fluxo de <xref:System.Windows.FlowDirection.RightToLeft> da <xref:System.Windows.Controls.StackPanel> de forma que seus pontos inicial e final sejam medidos de uma raiz no lado direito. A segunda seta que tem um <xref:System.Windows.FlowDirection.RightToLeft> explícito <xref:System.Windows.FlowDirection> também é iniciada no lado direito. No entanto, a terceira seta tem sua raiz inicial no lado esquerdo. Para obter mais informações sobre o desenho, consulte <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.GeometryGroup>.

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

O gráfico a seguir mostra a saída do exemplo anterior com setas desenhadas usando o elemento `Path`:

![Gráfico que ilustra as setas desenhadas usando o elemento Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

Os <xref:System.Windows.Controls.Image> e <xref:System.Windows.Shapes.Path> são dois exemplos de como [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] usa <xref:System.Windows.FlowDirection>. Ao lado do layout [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos em uma direção específica dentro de um contêiner, <xref:System.Windows.FlowDirection> pode ser usado com elementos como <xref:System.Windows.Controls.InkPresenter> que processa a tinta em uma superfície, <xref:System.Windows.Media.LinearGradientBrush><xref:System.Windows.Media.RadialGradientBrush>. Sempre que você precisar de um comportamento da direita para a esquerda para seu conteúdo que imita um comportamento da esquerda para a direita, ou vice-versa, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece esse recurso.

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>Substituição de números

Historicamente, o Windows tem suporte para substituição de números, permitindo a representação de diferentes formas culturais para os mesmos dígitos enquanto mantém o armazenamento interno desses dígitos unificados entre diferentes localidades, por exemplo, os números são armazenados em seus valores hexadecimais conhecidos, 0x40, 0x41, mas são exibidos de acordo com o idioma selecionado.

Isso permitiu que os aplicativos processassem valores numéricos sem a necessidade de convertê-los de um idioma para outro, por exemplo, um usuário pode abrir uma planilha do Microsoft Excel em um Windows árabe localizado e ver os números moldados em árabe, mas abri-los em um Versão europeia do Windows e ver a representação Europeia dos mesmos números. Isso também é necessário para outros símbolos, como separadores de vírgula e símbolo de percentual, porque eles geralmente acompanham os números no mesmo documento.

O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dá continuidade à mesma tradição e adiciona suporte adicional a esse recurso, o que permite maior controle do usuário sobre quando e como a substituição é usada. Embora esse recurso tenha sido projetado para qualquer idioma, ele é particularmente útil no conteúdo bidirecional, em que a formatação de dígitos de um idioma específico é, de modo geral, um desafio para os desenvolvedores de aplicativos, devido às várias culturas nas quais um aplicativo pode ser executado.

A propriedade Core que controla como a substituição de número funciona em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é a propriedade de dependência <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>. A classe <xref:System.Windows.Media.NumberSubstitution> especifica como os números no texto devem ser exibidos. Ela tem três propriedades públicas que definem seu comportamento. Veja a seguir um resumo de cada uma das propriedades:

**CultureSource:**

Essa propriedade especifica como a cultura para números é determinada. Ele usa um dos três <xref:System.Windows.Media.NumberCultureSource> valores de enumeração.

- Override: o número de cultura é o da propriedade <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>.

- Texto: a cultura dos números é a cultura da sequência de texto. Na marcação, isso seria `xml:lang`ou seu alias `Language` Propriedade (<xref:System.Windows.FrameworkElement.Language%2A> ou <xref:System.Windows.FrameworkContentElement.Language%2A>). Além disso, é o padrão para classes derivadas de <xref:System.Windows.FrameworkContentElement>. Essas classes incluem <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> e assim por diante.

- Usuário: a cultura dos números é a cultura do thread atual. Essa propriedade é o padrão para todas as subclasses de <xref:System.Windows.FrameworkElement> como <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> e <xref:System.Windows.Controls.TextBlock>.

**CultureOverride**:

A propriedade <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> será usada somente se a propriedade <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> estiver definida como <xref:System.Windows.Media.NumberCultureSource.Override> e for ignorada de outra forma. Ela especifica a cultura dos números. Um valor de `null`, o valor padrão, é interpretado como en-US.

**Substitution**:

Essa propriedade especifica o tipo de substituição de números a ser executado. Ele usa um dos seguintes <xref:System.Windows.Media.NumberSubstitutionMethod> valores de enumeração:

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: o método de substituição é determinado com base na propriedade <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> da cultura do número. Esse é o padrão.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: se a cultura do número for uma cultura árabe ou persa, ela especificará que os dígitos dependem do contexto.

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: os números são sempre renderizados como dígitos europeus.

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: os números são renderizados usando os dígitos nacionais para a cultura de número, conforme especificado pelo <xref:System.Globalization.CultureInfo.NumberFormat%2A>da cultura.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: os números são renderizados usando os dígitos tradicionais para a cultura do número. Para a maioria das culturas, isso é o mesmo que <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. No entanto, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> resulta em dígitos latinos para algumas culturas árabes, enquanto esse valor resulta em dígitos árabes para todas as culturas árabes.

O que esses valores significam para um desenvolvedor de conteúdo bidirecional? Na maioria dos casos, o desenvolvedor pode precisar apenas definir <xref:System.Windows.FlowDirection> e o idioma de cada elemento de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] textual, por exemplo `Language="ar-SA"` e a lógica de <xref:System.Windows.Media.NumberSubstitution> cuida de exibir os números de acordo com o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]correto. O exemplo a seguir demonstra o uso de números em árabe e em inglês em um aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] em execução em uma versão árabe do Windows.

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

O gráfico a seguir mostra a saída do exemplo anterior se você estiver executando em uma versão em árabe do Windows com os números árabe e inglês exibidos:

![Gráfico que mostra números em árabe e em inglês.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

O <xref:System.Windows.FlowDirection> era importante nesse caso porque definir a <xref:System.Windows.FlowDirection> como <xref:System.Windows.FlowDirection.LeftToRight>, em vez disso, teria um resultado de dígitos europeus. As próximas seções abordam como ter uma exibição unificada de dígitos em todo o documento. Se esse exemplo não estiver sendo executado no Windows em árabe, todos os dígitos serão exibidos como dígitos europeus.

**Definindo regras de substituição**

Em um aplicativo real, talvez você deseje definir o Idioma de forma programática. Por exemplo, você deseja definir o atributo `xml:lang` como o mesmo usado pelo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]do sistema, ou talvez alterar o idioma dependendo do estado do aplicativo.

Se você quiser fazer alterações com base no estado do aplicativo, use outros recursos fornecidos pelo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].

Primeiro, defina o `NumberSubstitution.CultureSource="Text"` do componente do aplicativo. O uso dessa configuração garante que as configurações não sejam provenientes da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para elementos de texto que tenham "user" como padrão, como <xref:System.Windows.Controls.TextBlock>.

Por exemplo:

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

No código correspondente C# , defina a propriedade `Language`, por exemplo, para `"ar-SA"`.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Se você precisar definir a propriedade `Language` para o idioma da interface do usuário atual, use o código a seguir.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> representa a cultura atual usada pelo thread atual em tempo de execução.

O exemplo de XAML final deve ser semelhante ao exemplo a seguir.

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

O exemplo C# final deve ser semelhante ao seguinte.

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

O gráfico a seguir mostra a aparência da janela para a linguagem de programação, exibindo números árabes:

![Gráfico que exibe os números árabes.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Usando a propriedade de substituição**

O modo como a substituição de número funciona no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] depende do idioma do elemento de texto e de sua <xref:System.Windows.FlowDirection>. Se a <xref:System.Windows.FlowDirection> for da esquerda para a direita, os dígitos europeus serão renderizados. No entanto, se ele for precedido por um texto em árabe ou tiver o idioma definido como "ar" e o <xref:System.Windows.FlowDirection> for <xref:System.Windows.FlowDirection.RightToLeft>, os dígitos árabes serão renderizados em vez disso.

No entanto, em alguns casos, talvez você deseje criar um aplicativo unificado, por exemplo, europeus dígitos para todos os usuários. Ou dígitos árabes em <xref:System.Windows.Documents.Table> células com um <xref:System.Windows.Style> específico. Uma maneira fácil de fazer isso é usando a propriedade <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>.

No exemplo a seguir, a primeira <xref:System.Windows.Controls.TextBlock> não tem a propriedade <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> definida, portanto, o algoritmo exibe os dígitos árabes conforme o esperado. No entanto, na segunda <xref:System.Windows.Controls.TextBlock>, a substituição é definida como European substituindo a substituição padrão por números árabes e os dígitos europeus são exibidos.

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
