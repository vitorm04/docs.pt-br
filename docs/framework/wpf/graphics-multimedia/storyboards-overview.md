---
title: Visão geral de storyboards
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 5c058dbaf2ae209a198a8299790d4002447ac443
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559684"
---
# <a name="storyboards-overview"></a>Visão geral de storyboards

Este tópico mostra como usar <xref:System.Windows.Media.Animation.Storyboard> objetos para organizar e aplicar animações. Ele descreve como manipular interativamente <xref:System.Windows.Media.Animation.Storyboard> objetos e descreve a sintaxe de direcionamento de propriedade indireta.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de animação e seus recursos básicos. Para obter uma introdução à animação, consulte a [Visão geral da animação](animation-overview.md). Você também deve saber usar propriedades anexadas. Para obter mais informações sobre as propriedades anexadas, consulte [Visão geral das propriedades anexadas](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>O que é um storyboard?

Animações não são o único tipo útil de linha do tempo. Outras classes de linha do tempo são fornecidas para ajudá-lo a organizar conjuntos de linhas do tempo e aplicar linhas do tempo a propriedades. As linhas do tempo do contêiner derivam da classe <xref:System.Windows.Media.Animation.TimelineGroup> e incluem <xref:System.Windows.Media.Animation.ParallelTimeline> e <xref:System.Windows.Media.Animation.Storyboard>.

Um <xref:System.Windows.Media.Animation.Storyboard> é um tipo de linha do tempo de contêiner que fornece informações de destino para os cronogramas que ele contém. Um storyboard pode conter qualquer tipo de <xref:System.Windows.Media.Animation.Timeline>, incluindo outras linhas do tempo e animações de contêiner. os objetos <xref:System.Windows.Media.Animation.Storyboard> permitem que você combine linhas do tempo que afetam uma variedade de objetos e propriedades em uma única árvore de linha cronológica, facilitando a organização e o controle de comportamentos de tempo complexos. Por exemplo, suponha que você deseje que um botão faça estas três coisas.

- Aumenta e muda de cor quando o usuário o seleciona.

- Diminui e, em seguida, aumenta novamente para seu tamanho original quando recebe um clique.

- Diminui e esmaece até uma opacidade de 50% quando é desabilitado.

Nesse caso, você tem vários conjuntos de animações que se aplicam ao mesmo objeto e deseja que eles sejam reproduzidos em tempos diferentes, dependentes do estado do botão. <xref:System.Windows.Media.Animation.Storyboard> objetos permitem organizar as animações e aplicá-las em grupos a um ou mais objetos.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Onde você pode usar um storyboard?

Um <xref:System.Windows.Media.Animation.Storyboard> pode ser usado para animar propriedades de dependência de classes animáveis (para obter mais informações sobre o que torna uma classe animável, consulte a [visão geral da animação](animation-overview.md)). No entanto, como o Storyboarding é um recurso de nível de estrutura, o objeto deve pertencer à <xref:System.Windows.NameScope> de um <xref:System.Windows.FrameworkElement> ou um <xref:System.Windows.FrameworkContentElement>.

Por exemplo, você pode usar um <xref:System.Windows.Media.Animation.Storyboard> para fazer o seguinte:

- Animar um <xref:System.Windows.Media.SolidColorBrush> (elemento não estrutura) que pinta o plano de fundo de um botão (um tipo de <xref:System.Windows.FrameworkElement>),

- Anime um <xref:System.Windows.Media.SolidColorBrush> (elemento não estrutura) que pinta o preenchimento de um <xref:System.Windows.Media.GeometryDrawing> (elemento não estrutura) exibido usando um <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).

- No código, anime um <xref:System.Windows.Media.SolidColorBrush> declarado por uma classe que também contém um <xref:System.Windows.FrameworkElement>, se o <xref:System.Windows.Media.SolidColorBrush> registrou seu nome com esse <xref:System.Windows.FrameworkElement>.

No entanto, você não pode usar um <xref:System.Windows.Media.Animation.Storyboard> para animar um <xref:System.Windows.Media.SolidColorBrush> que não registrou seu nome com um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, ou não foi usado para definir uma propriedade de um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Como aplicar animações com um storyboard

Para usar um <xref:System.Windows.Media.Animation.Storyboard> para organizar e aplicar animações, você adiciona as animações como cronogramas filho do <xref:System.Windows.Media.Animation.Storyboard>. A classe <xref:System.Windows.Media.Animation.Storyboard> fornece as propriedades <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> anexadas. Você pode definir essas propriedades em uma animação para especificar seu objeto de destino e sua propriedade.

Para aplicar animações a seus destinos, você começa a <xref:System.Windows.Media.Animation.Storyboard> usando uma ação de gatilho ou um método. No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você usa um objeto <xref:System.Windows.Media.Animation.BeginStoryboard> com um <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>ou <xref:System.Windows.DataTrigger>. No código, você também pode usar o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.

A tabela a seguir mostra os diferentes locais em que há suporte para cada técnica de início de <xref:System.Windows.Media.Animation.Storyboard>: por instância, estilo, modelo de controle e modelo de dados. "Por instância" se refere à técnica de aplicar uma animação ou storyboard diretamente às instâncias de um objeto, em vez de um estilo, modelo de controle ou modelo de dados.

|O storyboard é iniciado usando…|Por instância|Estilo|Modelo de controle|Modelo de dados|Exemplo|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard> e um <xref:System.Windows.EventTrigger>|Sim|Sim|Sim|Sim|[Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> e uma propriedade <xref:System.Windows.Trigger>|Não|Sim|Sim|Sim|[Disparar uma animação quando o valor de uma propriedade é alterado](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> e um <xref:System.Windows.DataTrigger>|Não|Sim|Sim|Sim|[Como disparar uma animação quando dados são alterados](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Sim|Não|Não|Não|[Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)|

O exemplo a seguir usa um <xref:System.Windows.Media.Animation.Storyboard> para animar a <xref:System.Windows.FrameworkElement.Width%2A> de um elemento <xref:System.Windows.Shapes.Rectangle> e a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para pintar esse <xref:System.Windows.Shapes.Rectangle>.

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

As seções a seguir descrevem as propriedades <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> anexadas mais detalhadamente.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Definindo como destino elementos de estrutura, elementos de conteúdo de estrutura e congeláveis

Na seção anterior, mencionamos que, para uma animação encontrar seu destino, ela deve saber o nome do destino e a propriedade a ser animada. A especificação da propriedade para animar é direta: basta definir <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> com o nome da propriedade a ser animada.  Especifique o nome do objeto cuja propriedade você deseja animar definindo a propriedade <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> na animação.

Para que a propriedade <xref:System.Windows.Setter.TargetName%2A> funcione, o objeto de destino deve ter um nome. Atribuir um nome a um <xref:System.Windows.FrameworkElement> ou a um <xref:System.Windows.FrameworkContentElement> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é diferente de atribuir um nome a um objeto <xref:System.Windows.Freezable>.

Os elementos da estrutura são as classes que herdam da classe <xref:System.Windows.FrameworkElement>. Exemplos de elementos de estrutura incluem <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>e <xref:System.Windows.Shapes.Rectangle>. Basicamente, todas as janelas, todos os painéis e todos os controles são elementos. Elementos de conteúdo da estrutura são as classes que herdam da classe <xref:System.Windows.FrameworkContentElement>. Exemplos de elementos de conteúdo de estrutura incluem <xref:System.Windows.Documents.FlowDocument> e <xref:System.Windows.Documents.Paragraph>. Se você não tiver certeza se um tipo é um elemento de estrutura ou um elemento de conteúdo de estrutura, verifique se ele tem uma propriedade Name. Se isso acontecer, provavelmente, ele será um elemento de estrutura ou um elemento de conteúdo de estrutura. Para ter certeza, confira a seção Hierarquia de herança da página de seu tipo.

Para habilitar o direcionamento de um elemento de estrutura ou um elemento de conteúdo de estrutura em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], defina sua propriedade <xref:System.Windows.FrameworkElement.Name%2A>. No código, você também precisa usar o método <xref:System.Windows.NameScope.RegisterName%2A> para registrar o nome do elemento com o elemento para o qual você criou uma <xref:System.Windows.NameScope>.

O exemplo a seguir, extraído do exemplo anterior, atribui o nome `MyRectangle` um <xref:System.Windows.Shapes.Rectangle>, um tipo de <xref:System.Windows.FrameworkElement>.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Depois que ele tiver um nome, você poderá animar uma propriedade desse elemento.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

os tipos de <xref:System.Windows.Freezable> são as classes que herdam da classe <xref:System.Windows.Freezable>. Exemplos de <xref:System.Windows.Freezable> incluem <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>e <xref:System.Windows.Media.GradientStop>.

Para habilitar o direcionamento de um <xref:System.Windows.Freezable> por uma animação no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use a [diretiva x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) para atribuir um nome a ele. No código, você usa o método <xref:System.Windows.NameScope.RegisterName%2A> para registrar seu nome com o elemento para o qual você criou uma <xref:System.Windows.NameScope>.

O exemplo a seguir atribui um nome a um objeto <xref:System.Windows.Freezable>.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Em seguida, o objeto pode ser o destino de uma animação.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard> objetos usam escopos de nome para resolver a propriedade <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>. Para obter mais informações sobre escopos de nome no WPF, consulte [Escopos de nome XAML no WPF](../advanced/wpf-xaml-namescopes.md). Se a propriedade <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> for omitida, a animação visará o elemento no qual ele está definido ou, no caso de estilos, o elemento com estilo.

Às vezes, um nome não pode ser atribuído a um objeto <xref:System.Windows.Freezable>. Por exemplo, se um <xref:System.Windows.Freezable> for declarado como um recurso ou usado para definir um valor de propriedade em um estilo, ele não poderá receber um nome. Como ele não tem um nome, ele não pode ser definido como destino diretamente – mas ele pode ser definido como destino indiretamente. As próximas seções descrevem como usar o direcionamento indireto.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Direcionamento indireto

Há ocasiões em que uma <xref:System.Windows.Freezable> não pode ser direcionada diretamente por uma animação, como quando a <xref:System.Windows.Freezable> é declarada como um recurso ou usada para definir um valor de propriedade em um estilo. Nesses casos, embora não seja possível direcioná-lo diretamente, você ainda pode animar o objeto <xref:System.Windows.Freezable>. Em vez de definir a propriedade <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> com o nome da <xref:System.Windows.Freezable>, você concede a ela o nome do elemento ao qual o <xref:System.Windows.Freezable> "pertence". Por exemplo, um <xref:System.Windows.Media.SolidColorBrush> usado para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> de um elemento Rectangle pertence a esse retângulo. Para animar o pincel, você definiria a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> da animação com uma cadeia de propriedades que começa na Propriedade do elemento de estrutura ou no elemento de conteúdo da estrutura, a <xref:System.Windows.Freezable> foi usada para definir e terminar com a propriedade <xref:System.Windows.Freezable> para animar.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Observe que, se a <xref:System.Windows.Freezable> estiver congelada, um clone será feito e esse clone será animado. Quando isso acontece, a propriedade <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> do objeto original continua a retornar `false`, porque o objeto original não é realmente animado. Para obter mais informações sobre a clonagem, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).

Observe também que, ao usar o direcionamento indireto de propriedade, é possível definir como destino objetos inexistentes. Por exemplo, você pode pressupor que a <xref:System.Windows.Controls.Control.Background%2A> de um botão específico foi definida com um <xref:System.Windows.Media.SolidColorBrush> e tentar animar sua cor, quando, na verdade, uma <xref:System.Windows.Media.LinearGradientBrush> foi usada para definir o plano de fundo do botão. Nesses casos, nenhuma exceção é lançada; a animação não tem um efeito visível porque <xref:System.Windows.Media.LinearGradientBrush> não reage às alterações na propriedade <xref:System.Windows.Media.SolidColorBrush.Color%2A>.

As próximas seções descrevem a sintaxe de direcionamento indireto de propriedade mais detalhadamente.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Definindo indiretamente como destino uma propriedade de um congelável em XAML

Para direcionar uma propriedade de um Freezable em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use a sintaxe a seguir.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Onde

- *ElementPropertyName* é a propriedade do <xref:System.Windows.FrameworkElement> que o <xref:System.Windows.Freezable> é usado para definir e

- *FreezablePropertyName* é a propriedade da <xref:System.Windows.Freezable> para animar.

O código a seguir mostra como animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para definir a <xref:System.Windows.Shapes.Shape.Fill%2A> de um elemento Rectangle.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Às vezes, você precisa ter como destino um congelável contido em uma coleção ou matriz.

Para definir um congelável como destino contido em uma coleção, use a sintaxe de caminho a seguir.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Em que *CollectionIndex* é o índice do objeto em sua matriz ou coleção.

Por exemplo, suponha que um retângulo tenha um recurso de <xref:System.Windows.Media.TransformGroup> aplicado à sua propriedade <xref:System.Windows.UIElement.RenderTransform%2A> e que você queira animar uma das transformações que ele contém.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

O código a seguir mostra como animar a propriedade <xref:System.Windows.Media.RotateTransform.Angle%2A> do <xref:System.Windows.Media.RotateTransform> mostrado no exemplo anterior.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Definindo indiretamente como destino uma propriedade de um congelável no código

No código, você cria um objeto <xref:System.Windows.PropertyPath>. Ao criar o <xref:System.Windows.PropertyPath>, você especifica um <xref:System.Windows.PropertyPath.Path%2A> e <xref:System.Windows.PropertyPath.PathParameters%2A>.

Para criar <xref:System.Windows.PropertyPath.PathParameters%2A>, você cria uma matriz do tipo <xref:System.Windows.DependencyProperty> que contém uma lista de campos de identificador de propriedade de dependência. O primeiro campo identificador é para a propriedade do <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> que o <xref:System.Windows.Freezable> é usado para definir. O campo próximo identificador representa a propriedade do <xref:System.Windows.Freezable> para o destino. Imagine-o como uma cadeia de propriedades que conecta o <xref:System.Windows.Freezable> ao objeto <xref:System.Windows.FrameworkElement>.

Veja a seguir um exemplo de uma cadeia de propriedades de dependência que tem como alvo a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> de um elemento Rectangle.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Você também precisa especificar um <xref:System.Windows.PropertyPath.Path%2A>. Uma <xref:System.Windows.PropertyPath.Path%2A> é uma <xref:System.String> que informa ao <xref:System.Windows.PropertyPath.Path%2A> como interpretar seu <xref:System.Windows.PropertyPath.PathParameters%2A>. Ele usa a sintaxe a seguir.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Onde

- *OwnerPropertyArrayIndex* é o índice da matriz de <xref:System.Windows.DependencyProperty> que contém o identificador da Propriedade do objeto <xref:System.Windows.FrameworkElement> que o <xref:System.Windows.Freezable> é usado para definir e

- *FreezablePropertyArrayIndex* é o índice da matriz de <xref:System.Windows.DependencyProperty> que contém o identificador da propriedade a ser direcionada.

O exemplo a seguir mostra o <xref:System.Windows.PropertyPath.Path%2A> que acompanharia o <xref:System.Windows.PropertyPath.PathParameters%2A> definido no exemplo anterior.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

O exemplo a seguir combina o código nos exemplos anteriores para animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> de um elemento Rectangle.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Às vezes, você precisa ter como destino um congelável contido em uma coleção ou matriz. Por exemplo, suponha que um retângulo tenha um recurso de <xref:System.Windows.Media.TransformGroup> aplicado à sua propriedade <xref:System.Windows.UIElement.RenderTransform%2A> e que você queira animar uma das transformações que ele contém.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Para direcionar uma <xref:System.Windows.Freezable> contida em uma coleção, use a seguinte sintaxe de caminho.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

Em que *CollectionIndex* é o índice do objeto em sua matriz ou coleção.

Para direcionar a propriedade <xref:System.Windows.Media.RotateTransform.Angle%2A> da <xref:System.Windows.Media.RotateTransform>, a segunda transformação na <xref:System.Windows.Media.TransformGroup>, você usaria as seguintes <xref:System.Windows.PropertyPath.Path%2A> e <xref:System.Windows.PropertyPath.PathParameters%2A>.

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

O exemplo a seguir mostra o código completo para animar a <xref:System.Windows.Media.RotateTransform.Angle%2A> de um <xref:System.Windows.Media.RotateTransform> contido em uma <xref:System.Windows.Media.TransformGroup>.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Definindo indiretamente como destino um congelável como o ponto de partida

As seções anteriores descreveram como direcionar indiretamente um <xref:System.Windows.Freezable> iniciando com um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> e criando uma cadeia de propriedades para uma subpropriedade <xref:System.Windows.Freezable>. Você também pode usar uma <xref:System.Windows.Freezable> como um ponto de partida e direcionar indiretamente uma de suas subpropriedades <xref:System.Windows.Freezable>. Uma restrição adicional se aplica ao usar um <xref:System.Windows.Freezable> como ponto de partida para direcionamento indireto: o <xref:System.Windows.Freezable> inicial e cada <xref:System.Windows.Freezable> entre ele e a subpropriedade de destino indiretamente não deve ser congelada.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Controlando um storyboard de forma interativa no XAML

Para iniciar um storyboard em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você usa uma ação de gatilho <xref:System.Windows.Media.Animation.BeginStoryboard>. <xref:System.Windows.Media.Animation.BeginStoryboard> distribui as animações para os objetos e as propriedades que eles animam e inicia o storyboard. (Para obter detalhes sobre esse processo, consulte a [visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md).) Se você fornecer o <xref:System.Windows.Media.Animation.BeginStoryboard> um nome especificando sua propriedade <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>, você o tornará um storyboard controlável. Você poderá então controlar o storyboard de forma interativa depois que ele for iniciado. Veja a seguir uma lista de ações de storyboard controlável usadas com gatilhos de evento para controlar um storyboard.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: pausa o storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: retoma um storyboard pausado.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: altera a velocidade do storyboard.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: avança um storyboard até o final de seu período de preenchimento, se ele tiver um.

- <xref:System.Windows.Media.Animation.StopStoryboard>: para o storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Remove o storyboard.

No exemplo a seguir, as ações de storyboard controlável são usadas para controlar um storyboard de forma interativa.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Controlando um storyboard de forma interativa usando um código

Os exemplos anteriores mostraram como animar usando ações de gatilho. No código, você também pode controlar um storyboard usando métodos interativos da classe <xref:System.Windows.Media.Animation.Storyboard>. Para que um <xref:System.Windows.Media.Animation.Storyboard> se torne interativo no código, você deve usar a sobrecarga apropriada do método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> do storyboard e especificar `true` para torná-lo controlável. Consulte a página <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> para obter mais informações.

A lista a seguir mostra os métodos que podem ser usados para manipular um <xref:System.Windows.Media.Animation.Storyboard> depois de iniciado:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

A vantagem de usar esses métodos é que você não precisa criar objetos <xref:System.Windows.Trigger> ou <xref:System.Windows.TriggerAction>; Você só precisa de uma referência ao <xref:System.Windows.Media.Animation.Storyboard> controlável que deseja manipular.

> [!NOTE]
> Todas as ações interativas executadas em um <xref:System.Windows.Media.Animation.Clock>e, portanto, também em um <xref:System.Windows.Media.Animation.Storyboard> ocorrerão no próximo tique do mecanismo de tempo que ocorrerá logo antes da próxima renderização. Por exemplo, se você usar o método <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> para saltar para outro ponto em uma animação, o valor da propriedade não será alterado instantaneamente, em vez disso, o valor será alterado no próximo tique do mecanismo de tempo.

O exemplo a seguir mostra como aplicar e controlar animações usando os métodos interativos da classe <xref:System.Windows.Media.Animation.Storyboard>.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animar em um estilo

Você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para definir animações em um <xref:System.Windows.Style>. A animação com um <xref:System.Windows.Media.Animation.Storyboard> em uma <xref:System.Windows.Style> é semelhante ao uso de um <xref:System.Windows.Media.Animation.Storyboard> em outro lugar, com as três seguintes exceções:

- Você não especifica um <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; o <xref:System.Windows.Media.Animation.Storyboard> sempre tem como alvo o elemento ao qual o <xref:System.Windows.Style> é aplicado. Para direcionar os objetos de <xref:System.Windows.Freezable>, você deve usar o direcionamento indireto. Para obter mais informações sobre direcionamento indireto, consulte a seção [direcionamento indireto](#pathsyntaxforchangeable) .

- Você não pode especificar um <xref:System.Windows.EventTrigger.SourceName%2A> para um <xref:System.Windows.EventTrigger> ou um <xref:System.Windows.Trigger>.

- Você não pode usar referências de recursos dinâmicos ou expressões de associação de dados para definir <xref:System.Windows.Media.Animation.Storyboard> ou valores de propriedade de animação. Isso ocorre porque tudo dentro de um <xref:System.Windows.Style> deve ser thread-safe e o sistema de tempo deve <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> objetos para torná-los thread-safe. Um <xref:System.Windows.Media.Animation.Storyboard> não pode ser congelado se ele ou suas linhas do tempo filho contêm referências de recursos dinâmicos ou expressões de associação de dados. Para obter mais informações sobre como congelar e outros recursos <xref:System.Windows.Freezable>, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).

- No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você não pode declarar manipuladores de eventos para <xref:System.Windows.Media.Animation.Storyboard> ou eventos de animação.

Para obter um exemplo que mostra como definir um storyboard em um estilo, consulte o exemplo de [animar em um estilo](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Animar em um ControlTemplate

Você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para definir animações em um <xref:System.Windows.Controls.ControlTemplate>. A animação com um <xref:System.Windows.Media.Animation.Storyboard> em uma <xref:System.Windows.Controls.ControlTemplate> é semelhante ao uso de um <xref:System.Windows.Media.Animation.Storyboard> em outro lugar, com as duas exceções a seguir:

- A <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> só pode se referir a objetos filho da <xref:System.Windows.Controls.ControlTemplate>. Se <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> não for especificado, a animação se destinará ao elemento ao qual o <xref:System.Windows.Controls.ControlTemplate> é aplicado.

- O <xref:System.Windows.EventTrigger.SourceName%2A> para um <xref:System.Windows.EventTrigger> ou um <xref:System.Windows.Trigger> só pode se referir a objetos filho da <xref:System.Windows.Controls.ControlTemplate>.

- Você não pode usar referências de recursos dinâmicos ou expressões de associação de dados para definir <xref:System.Windows.Media.Animation.Storyboard> ou valores de propriedade de animação. Isso ocorre porque tudo dentro de um <xref:System.Windows.Controls.ControlTemplate> deve ser thread-safe e o sistema de tempo deve <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> objetos para torná-los thread-safe. Um <xref:System.Windows.Media.Animation.Storyboard> não pode ser congelado se ele ou suas linhas do tempo filho contêm referências de recursos dinâmicos ou expressões de associação de dados. Para obter mais informações sobre como congelar e outros recursos <xref:System.Windows.Freezable>, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).

- No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você não pode declarar manipuladores de eventos para <xref:System.Windows.Media.Animation.Storyboard> ou eventos de animação.

Para obter um exemplo que mostra como definir um storyboard em um <xref:System.Windows.Controls.ControlTemplate>, consulte o exemplo de [animar em um ControlTemplate](how-to-animate-in-a-controltemplate.md) .

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animar quando um valor da propriedade é alterado

Em estilos e modelos de controle, você pode usar objetos Trigger para iniciar um storyboard quando uma propriedade é alterada. Para obter exemplos, consulte [disparar uma animação quando um valor de propriedade for alterado](how-to-trigger-an-animation-when-a-property-value-changes.md) e [animar em um ControlTemplate](how-to-animate-in-a-controltemplate.md).

As animações aplicadas pelos objetos de <xref:System.Windows.Trigger> de propriedades se comportam de maneira mais complexa do que <xref:System.Windows.EventTrigger> animações ou animações iniciadas usando métodos <xref:System.Windows.Media.Animation.Storyboard>.  Eles "entregam" com animações definidas por outros objetos de <xref:System.Windows.Trigger>, mas compõem <xref:System.Windows.EventTrigger> e animações disparadas por método.

## <a name="see-also"></a>Veja também

- [Visão geral da animação](animation-overview.md)
- [Visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
