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
ms.openlocfilehash: 4d5a5ee3f1fcbd09fad9e25773d0e508209e1492
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855845"
---
# <a name="storyboards-overview"></a>Visão geral de storyboards

Este tópico mostra como usar <xref:System.Windows.Media.Animation.Storyboard> objetos para organizar e aplicar animações. Ele descreve como manipular <xref:System.Windows.Media.Animation.Storyboard> objetos interativamente e descreve a sintaxe de direcionamento de propriedade indireta.

## <a name="prerequisites"></a>Pré-requisitos

Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de animação e seus recursos básicos. Para obter uma introdução à animação, consulte a [Visão geral da animação](animation-overview.md). Você também deve saber usar propriedades anexadas. Para obter mais informações sobre as propriedades anexadas, consulte [Visão geral das propriedades anexadas](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>O que é um storyboard?

Animações não são o único tipo útil de linha do tempo. Outras classes de linha do tempo são fornecidas para ajudá-lo a organizar conjuntos de linhas do tempo e aplicar linhas do tempo a propriedades. As <xref:System.Windows.Media.Animation.TimelineGroup> linhas do tempo do contêiner derivam da classe e <xref:System.Windows.Media.Animation.ParallelTimeline> incluem <xref:System.Windows.Media.Animation.Storyboard>e.

Um <xref:System.Windows.Media.Animation.Storyboard> é um tipo de linha do tempo de contêiner que fornece informações de destino para os cronogramas que ele contém. Um storyboard pode conter qualquer tipo de <xref:System.Windows.Media.Animation.Timeline>, incluindo outras linhas do tempo e animações de contêiner. <xref:System.Windows.Media.Animation.Storyboard>os objetos permitem combinar cronogramas que afetam uma variedade de objetos e propriedades em uma única árvore de linha do tempo, facilitando a organização e o controle de comportamentos de tempo complexos. Por exemplo, suponha que você deseje que um botão faça estas três coisas.

- Aumenta e muda de cor quando o usuário o seleciona.

- Diminui e, em seguida, aumenta novamente para seu tamanho original quando recebe um clique.

- Diminui e esmaece até uma opacidade de 50% quando é desabilitado.

Nesse caso, você tem vários conjuntos de animações que se aplicam ao mesmo objeto e deseja que eles sejam reproduzidos em tempos diferentes, dependentes do estado do botão. <xref:System.Windows.Media.Animation.Storyboard>os objetos permitem organizar as animações e aplicá-las em grupos a um ou mais objetos.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Onde você pode usar um storyboard?

Um <xref:System.Windows.Media.Animation.Storyboard> pode ser usado para animar propriedades de dependência de classes animáveis (para obter mais informações sobre o que torna uma classe animável, consulte a [visão geral da animação](animation-overview.md)). No entanto, como o <xref:System.Windows.NameScope> Storyboarding é um recurso de nível de estrutura, o objeto deve pertencer ao de um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>a.

Por exemplo, você pode usar um <xref:System.Windows.Media.Animation.Storyboard> para fazer o seguinte:

- Animar <xref:System.Windows.Media.SolidColorBrush> um (elemento não estrutura) que pinta o plano de fundo de um botão (um <xref:System.Windows.FrameworkElement>tipo de),

- Anime um <xref:System.Windows.Media.SolidColorBrush> (elemento não estrutura) que pinta o preenchimento de um <xref:System.Windows.Media.GeometryDrawing> (elemento não estrutura) exibido usando um <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).

- No código, anime um <xref:System.Windows.Media.SolidColorBrush> declarado por uma classe que também contém um <xref:System.Windows.FrameworkElement>, se o <xref:System.Windows.Media.SolidColorBrush> registrou seu nome com <xref:System.Windows.FrameworkElement>ele.

No entanto, você não pode <xref:System.Windows.Media.Animation.Storyboard> usar um para <xref:System.Windows.Media.SolidColorBrush> animar um que não registrou seu <xref:System.Windows.FrameworkElement> nome <xref:System.Windows.FrameworkContentElement>com um ou, ou não foi usado para definir uma <xref:System.Windows.FrameworkElement> propriedade <xref:System.Windows.FrameworkContentElement>de um ou.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Como aplicar animações com um storyboard

Para usar um <xref:System.Windows.Media.Animation.Storyboard> para organizar e aplicar animações, você adiciona as animações como linhas <xref:System.Windows.Media.Animation.Storyboard>do tempo filho do. A <xref:System.Windows.Media.Animation.Storyboard> classe fornece as <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> propriedades <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> anexadas e. Você pode definir essas propriedades em uma animação para especificar seu objeto de destino e sua propriedade.

Para aplicar animações a seus destinos, você começa a <xref:System.Windows.Media.Animation.Storyboard> usar uma ação de gatilho ou um método. No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você usa um <xref:System.Windows.Media.Animation.BeginStoryboard> objeto com um <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>ou <xref:System.Windows.DataTrigger>. No código, você também pode usar o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método.

A tabela a seguir mostra os diferentes locais em <xref:System.Windows.Media.Animation.Storyboard> que há suporte para cada técnica de início: por instância, estilo, modelo de controle e modelo de dados. "Por instância" se refere à técnica de aplicar uma animação ou storyboard diretamente às instâncias de um objeto, em vez de um estilo, modelo de controle ou modelo de dados.

|O storyboard é iniciado usando…|Por instância|Estilo|Modelo de controle|Modelo de dados|Exemplo|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.EventTrigger>|Sim|Sim|Sim|Sim|[Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>e uma propriedade<xref:System.Windows.Trigger>|Não|Sim|Sim|Sim|[Disparar uma animação quando o valor de uma propriedade é alterado](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.DataTrigger>|Não|Sim|Sim|Sim|[Como: Disparar uma animação quando os dados forem alterados](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Sim|Não|Não|Não|[Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)|

O exemplo a seguir usa <xref:System.Windows.Media.Animation.Storyboard> um para animar o <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> de um elemento <xref:System.Windows.Media.SolidColorBrush.Color%2A> e o <xref:System.Windows.Media.SolidColorBrush> de um usado para <xref:System.Windows.Shapes.Rectangle>pintar isso.

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

As seções a seguir descrevem <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> as <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> Propriedades e anexadas em mais detalhes.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Definindo como destino elementos de estrutura, elementos de conteúdo de estrutura e congeláveis

Na seção anterior, mencionamos que, para uma animação encontrar seu destino, ela deve saber o nome do destino e a propriedade a ser animada. A especificação da propriedade a ser animada é direta: basta <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> definir com o nome da propriedade para animar.  Especifique o nome do objeto cuja propriedade você deseja animar definindo a <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> Propriedade na animação.

Para que <xref:System.Windows.Setter.TargetName%2A> a propriedade funcione, o objeto de destino deve ter um nome. Atribuir um <xref:System.Windows.FrameworkElement> nome a um ou a <xref:System.Windows.FrameworkContentElement> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é diferente de atribuir um nome a um <xref:System.Windows.Freezable> objeto.

Os elementos da estrutura são as classes que herdam da <xref:System.Windows.FrameworkElement> classe. Exemplos de elementos de estrutura <xref:System.Windows.Window>incluem <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Button>,, e <xref:System.Windows.Shapes.Rectangle>. Basicamente, todas as janelas, todos os painéis e todos os controles são elementos. Elementos de conteúdo da estrutura são as classes que herdam da <xref:System.Windows.FrameworkContentElement> classe. Exemplos de elementos de conteúdo de <xref:System.Windows.Documents.FlowDocument> estrutura <xref:System.Windows.Documents.Paragraph>incluem e. Se você não tiver certeza se um tipo é um elemento de estrutura ou um elemento de conteúdo de estrutura, verifique se ele tem uma propriedade Name. Se isso acontecer, provavelmente, ele será um elemento de estrutura ou um elemento de conteúdo de estrutura. Para ter certeza, confira a seção Hierarquia de herança da página de seu tipo.

Para habilitar o direcionamento de um elemento de estrutura ou um elemento de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]conteúdo de estrutura no <xref:System.Windows.FrameworkElement.Name%2A> , defina sua propriedade. No código, você também precisa usar o <xref:System.Windows.NameScope.RegisterName%2A> método para registrar o nome do elemento com o elemento para o qual você criou um. <xref:System.Windows.NameScope>

O exemplo a seguir, extraído do exemplo anterior, atribui o nome `MyRectangle` <xref:System.Windows.Shapes.Rectangle>a, um tipo de <xref:System.Windows.FrameworkElement>.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Depois que ele tiver um nome, você poderá animar uma propriedade desse elemento.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>os tipos são as classes que herdam <xref:System.Windows.Freezable> da classe. Exemplos de <xref:System.Windows.Freezable> include <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>e .<xref:System.Windows.Media.GradientStop>

Para habilitar o direcionamento de <xref:System.Windows.Freezable> um por uma animação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]no, use a [diretiva x:Name](../../xaml-services/x-name-directive.md) para atribuir um nome a ele. No código, você usa o <xref:System.Windows.NameScope.RegisterName%2A> método para registrar seu nome com o elemento para o qual você criou um <xref:System.Windows.NameScope>.

O exemplo a seguir atribui um nome a um <xref:System.Windows.Freezable> objeto.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Em seguida, o objeto pode ser o destino de uma animação.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>os objetos usam escopos de nome <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> para resolver a propriedade. Para obter mais informações sobre escopos de nome no WPF, consulte [Escopos de nome XAML no WPF](../advanced/wpf-xaml-namescopes.md). Se a <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriedade for omitida, a animação visará o elemento no qual ele está definido ou, no caso de estilos, o elemento com estilo.

Às vezes, um nome não pode ser <xref:System.Windows.Freezable> atribuído a um objeto. Por exemplo, se um <xref:System.Windows.Freezable> for declarado como um recurso ou usado para definir um valor de propriedade em um estilo, ele não poderá receber um nome. Como ele não tem um nome, ele não pode ser definido como destino diretamente – mas ele pode ser definido como destino indiretamente. As próximas seções descrevem como usar o direcionamento indireto.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Direcionamento indireto

Há ocasiões em que <xref:System.Windows.Freezable> um não pode ser direcionado diretamente por uma animação, como <xref:System.Windows.Freezable> quando o é declarado como um recurso ou usado para definir um valor de propriedade em um estilo. Nesses casos, embora não seja possível direcioná-lo diretamente, você ainda pode animar <xref:System.Windows.Freezable> o objeto. Em vez de definir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a propriedade com o nome <xref:System.Windows.Freezable>do, você atribui a ela o nome do elemento ao qual o <xref:System.Windows.Freezable> "pertence". Por exemplo, um <xref:System.Windows.Media.SolidColorBrush> usado para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> de um elemento Rectangle pertence a esse retângulo. Para animar o pincel, você definiria a animação <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> com uma cadeia de propriedades que começa na Propriedade do elemento do Framework ou do conteúdo do <xref:System.Windows.Freezable> Framework que foi usado para definir e terminar com a <xref:System.Windows.Freezable> Propriedade a ser animada.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Observe que, se o <xref:System.Windows.Freezable> estiver congelado, será feito um clone e esse clone será animado. Quando isso acontece, a propriedade do <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> objeto original continua a retornar `false`, pois o objeto original não é realmente animado. Para obter mais informações sobre a clonagem, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).

Observe também que, ao usar o direcionamento indireto de propriedade, é possível definir como destino objetos inexistentes. Por exemplo, você pode pressupor que <xref:System.Windows.Controls.Control.Background%2A> o de um botão específico foi definido com <xref:System.Windows.Media.SolidColorBrush> um e tentar animar sua cor, quando, na <xref:System.Windows.Media.LinearGradientBrush> verdade, um foi usado para definir o plano de fundo do botão. Nesses casos, nenhuma exceção é lançada; a animação não tem um efeito visível porque <xref:System.Windows.Media.LinearGradientBrush> não reage às alterações <xref:System.Windows.Media.SolidColorBrush.Color%2A> na propriedade.

As próximas seções descrevem a sintaxe de direcionamento indireto de propriedade mais detalhadamente.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Definindo indiretamente como destino uma propriedade de um congelável em XAML

Para direcionar uma propriedade de um Freezable [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]em, use a sintaxe a seguir.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Where

- *ElementPropertyName* é a propriedade da <xref:System.Windows.FrameworkElement> qual o <xref:System.Windows.Freezable> é usado para definir e

- *FreezablePropertyName* é a propriedade do <xref:System.Windows.Freezable> a ser animada.

O código a seguir mostra como animar <xref:System.Windows.Media.SolidColorBrush.Color%2A> o de <xref:System.Windows.Media.SolidColorBrush> um usado para definir <xref:System.Windows.Shapes.Shape.Fill%2A> o de um elemento Rectangle.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Às vezes, você precisa ter como destino um congelável contido em uma coleção ou matriz.

Para definir um congelável como destino contido em uma coleção, use a sintaxe de caminho a seguir.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Em que *CollectionIndex* é o índice do objeto em sua matriz ou coleção.

Por exemplo, suponha que um retângulo tenha um <xref:System.Windows.Media.TransformGroup> recurso aplicado à sua <xref:System.Windows.UIElement.RenderTransform%2A> Propriedade e você queira animar uma das transformações que ele contém.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

O código a seguir mostra como animar <xref:System.Windows.Media.RotateTransform.Angle%2A> a propriedade <xref:System.Windows.Media.RotateTransform> do mostrado no exemplo anterior.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Definindo indiretamente como destino uma propriedade de um congelável no código

No código, você cria um <xref:System.Windows.PropertyPath> objeto. Ao criar o <xref:System.Windows.PropertyPath>, você especifica um <xref:System.Windows.PropertyPath.Path%2A> e <xref:System.Windows.PropertyPath.PathParameters%2A>.

Para criar <xref:System.Windows.PropertyPath.PathParameters%2A>, você cria uma matriz do tipo <xref:System.Windows.DependencyProperty> que contém uma lista de campos de identificador de propriedade de dependência. O primeiro campo identificador é para a propriedade do <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> que o <xref:System.Windows.Freezable> é usado para definir. O campo próximo identificador representa a propriedade do <xref:System.Windows.Freezable> destino para. Imagine-o como uma cadeia de propriedades que conecta o <xref:System.Windows.Freezable> <xref:System.Windows.FrameworkElement> ao objeto.

Veja a seguir um exemplo de uma cadeia de propriedades de dependência que <xref:System.Windows.Media.SolidColorBrush.Color%2A> tem como <xref:System.Windows.Media.SolidColorBrush> alvo o de um <xref:System.Windows.Shapes.Shape.Fill%2A> usado para definir o de um elemento Rectangle.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Você também precisa especificar um <xref:System.Windows.PropertyPath.Path%2A>. Um <xref:System.Windows.PropertyPath.Path%2A> é um <xref:System.String> que diz <xref:System.Windows.PropertyPath.Path%2A> como interpretar seu <xref:System.Windows.PropertyPath.PathParameters%2A>. Ele usa a sintaxe a seguir.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Where

- *OwnerPropertyArrayIndex* é o índice da <xref:System.Windows.DependencyProperty> matriz que contém <xref:System.Windows.FrameworkElement> o identificador da Propriedade do objeto que o <xref:System.Windows.Freezable> é usado para definir e

- *FreezablePropertyArrayIndex* é o índice da <xref:System.Windows.DependencyProperty> matriz que contém o identificador da propriedade a ser direcionada.

O exemplo a seguir mostra <xref:System.Windows.PropertyPath.Path%2A> o que acompanharia <xref:System.Windows.PropertyPath.PathParameters%2A> o definido no exemplo anterior.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

O exemplo a seguir combina o código nos exemplos anteriores para animar <xref:System.Windows.Media.SolidColorBrush.Color%2A> o de <xref:System.Windows.Media.SolidColorBrush> um usado para definir <xref:System.Windows.Shapes.Shape.Fill%2A> o de um elemento Rectangle.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Às vezes, você precisa ter como destino um congelável contido em uma coleção ou matriz. Por exemplo, suponha que um retângulo tenha um <xref:System.Windows.Media.TransformGroup> recurso aplicado à sua <xref:System.Windows.UIElement.RenderTransform%2A> Propriedade e você queira animar uma das transformações que ele contém.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Para direcionar <xref:System.Windows.Freezable> um contido em uma coleção, use a seguinte sintaxe de caminho.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

Em que *CollectionIndex* é o índice do objeto em sua matriz ou coleção.

Para direcionar <xref:System.Windows.Media.RotateTransform.Angle%2A> a propriedade <xref:System.Windows.Media.RotateTransform>do, <xref:System.Windows.Media.TransformGroup>a segunda transformação no, você usaria o seguinte <xref:System.Windows.PropertyPath.Path%2A> e <xref:System.Windows.PropertyPath.PathParameters%2A>.

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

O exemplo a seguir mostra o código completo para animar <xref:System.Windows.Media.RotateTransform.Angle%2A> o <xref:System.Windows.Media.RotateTransform> de um contido <xref:System.Windows.Media.TransformGroup>em um.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Definindo indiretamente como destino um congelável como o ponto de partida

As seções anteriores descreveram como direcionar indiretamente um <xref:System.Windows.Freezable> iniciando com um <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.FrameworkElement> ou e criando uma cadeia de propriedades <xref:System.Windows.Freezable> para uma subpropriedade. Você também pode usar um <xref:System.Windows.Freezable> como ponto de partida e direcionar indiretamente uma <xref:System.Windows.Freezable> de suas subpropriedades. Uma restrição adicional se aplica ao usar <xref:System.Windows.Freezable> um como ponto de partida para direcionamento indireto <xref:System.Windows.Freezable> : o <xref:System.Windows.Freezable> início e todo entre ele e a subpropriedade de destino indiretamente não devem ser congeladas.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Controlando um storyboard de forma interativa no XAML

Para iniciar um storyboard no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você usa uma <xref:System.Windows.Media.Animation.BeginStoryboard> ação de gatilho. <xref:System.Windows.Media.Animation.BeginStoryboard>distribui as animações para os objetos e as propriedades que eles animam e inicia o storyboard. (Para obter detalhes sobre esse processo, consulte a [visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md).) Se você der <xref:System.Windows.Media.Animation.BeginStoryboard> um nome especificando sua <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> Propriedade, você o tornará um storyboard controlável. Você poderá então controlar o storyboard de forma interativa depois que ele for iniciado. Veja a seguir uma lista de ações de storyboard controlável usadas com gatilhos de evento para controlar um storyboard.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Altera a velocidade do storyboard.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avança um storyboard até o final de seu período de preenchimento, se ele tiver um.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Para o storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Remove o storyboard.

No exemplo a seguir, as ações de storyboard controlável são usadas para controlar um storyboard de forma interativa.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Controlando um storyboard de forma interativa usando um código

Os exemplos anteriores mostraram como animar usando ações de gatilho. No código, você também pode controlar um storyboard usando métodos interativos <xref:System.Windows.Media.Animation.Storyboard> da classe. Para que se torne interativo no código, você deve usar a sobrecarga apropriada do método do <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> storyboard e especificar `true` para torná-lo controlável. <xref:System.Windows.Media.Animation.Storyboard> Consulte a <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> página para obter mais informações.

A lista a seguir mostra os métodos que podem ser usados para manipular <xref:System.Windows.Media.Animation.Storyboard> um depois de iniciado:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

A vantagem de usar esses métodos é que você não precisa criar <xref:System.Windows.Trigger> objetos ou <xref:System.Windows.TriggerAction> ; você só precisa de uma referência para o controlável <xref:System.Windows.Media.Animation.Storyboard> que deseja manipular.

> [!NOTE]
> Todas as ações interativas <xref:System.Windows.Media.Animation.Clock>executadas em um e, portanto <xref:System.Windows.Media.Animation.Storyboard> , também ocorrerão no próximo tique do mecanismo de tempo que ocorrerá logo antes da próxima renderização. Por exemplo, se você usar o <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método para saltar para outro ponto em uma animação, o valor da propriedade não será alterado instantaneamente, em vez disso, o valor será alterado no próximo tique do mecanismo de tempo.

O exemplo a seguir mostra como aplicar e controlar animações usando os métodos interativos <xref:System.Windows.Media.Animation.Storyboard> da classe.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animar em um estilo

Você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para definir animações em um <xref:System.Windows.Style>. Animar com <xref:System.Windows.Media.Animation.Storyboard> um em <xref:System.Windows.Style> um é semelhante a usar <xref:System.Windows.Media.Animation.Storyboard> um em outro lugar, com as três seguintes exceções:

- Você não especifica um <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; o <xref:System.Windows.Media.Animation.Storyboard> sempre tem como alvo o elemento ao <xref:System.Windows.Style> qual o é aplicado. Para os <xref:System.Windows.Freezable> objetos de destino, você deve usar o direcionamento indireto. Para obter mais informações sobre direcionamento indireto, consulte a seção [direcionamento indireto](#pathsyntaxforchangeable) .

- Você não pode especificar <xref:System.Windows.EventTrigger.SourceName%2A> um <xref:System.Windows.EventTrigger> para um ou <xref:System.Windows.Trigger>um.

- Você não pode usar referências de recursos dinâmicos ou expressões de <xref:System.Windows.Media.Animation.Storyboard> Associação de dados para definir ou valores de propriedade de animação. Isso porque tudo dentro de um <xref:System.Windows.Style> deve ser thread-safe e o sistema de tempo deve <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> conter objetos para torná-los thread-safe. Um <xref:System.Windows.Media.Animation.Storyboard> não poderá ser congelado se ele ou suas linhas do tempo filho contiverem referências de recursos dinâmicos ou expressões de associação de dados. Para obter mais informações sobre congelamento e <xref:System.Windows.Freezable> outros recursos, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).

- No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você não pode declarar manipuladores de <xref:System.Windows.Media.Animation.Storyboard> eventos para eventos de animação ou.

Para obter um exemplo que mostra como definir um storyboard em um estilo, consulte o exemplo de [animar em um estilo](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Animar em um ControlTemplate

Você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para definir animações em um <xref:System.Windows.Controls.ControlTemplate>. Animar com <xref:System.Windows.Media.Animation.Storyboard> um em <xref:System.Windows.Controls.ControlTemplate> um é semelhante a usar <xref:System.Windows.Media.Animation.Storyboard> um em outro lugar, com as duas exceções a seguir:

- O <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> só pode se referir a objetos filho <xref:System.Windows.Controls.ControlTemplate>do. Se <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> não for especificado, a animação será direcionada ao elemento ao <xref:System.Windows.Controls.ControlTemplate> qual o é aplicado.

- O <xref:System.Windows.EventTrigger.SourceName%2A> para um <xref:System.Windows.EventTrigger> ou um <xref:System.Windows.Trigger> só <xref:System.Windows.Controls.ControlTemplate>pode se referir a objetos filho do.

- Você não pode usar referências de recursos dinâmicos ou expressões de <xref:System.Windows.Media.Animation.Storyboard> Associação de dados para definir ou valores de propriedade de animação. Isso porque tudo dentro de um <xref:System.Windows.Controls.ControlTemplate> deve ser thread-safe e o sistema de tempo deve <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> conter objetos para torná-los thread-safe. Um <xref:System.Windows.Media.Animation.Storyboard> não poderá ser congelado se ele ou suas linhas do tempo filho contiverem referências de recursos dinâmicos ou expressões de associação de dados. Para obter mais informações sobre congelamento e <xref:System.Windows.Freezable> outros recursos, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).

- No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você não pode declarar manipuladores de <xref:System.Windows.Media.Animation.Storyboard> eventos para eventos de animação ou.

Para obter um exemplo que mostra como definir um storyboard em <xref:System.Windows.Controls.ControlTemplate>um, consulte o exemplo de [animar em um ControlTemplate](how-to-animate-in-a-controltemplate.md) .

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animar quando um valor da propriedade é alterado

Em estilos e modelos de controle, você pode usar objetos Trigger para iniciar um storyboard quando uma propriedade é alterada. Para obter exemplos, consulte [disparar uma animação quando um valor de propriedade for alterado](how-to-trigger-an-animation-when-a-property-value-changes.md) e [animar em um ControlTemplate](how-to-animate-in-a-controltemplate.md).

As animações aplicadas por <xref:System.Windows.Trigger> objetos de propriedade se comportam de <xref:System.Windows.EventTrigger> maneira mais complexa do que <xref:System.Windows.Media.Animation.Storyboard> animações ou animações iniciadas usando métodos.  Eles "entregam" com animações definidas por <xref:System.Windows.Trigger> outros objetos, mas <xref:System.Windows.EventTrigger> compõem e animações disparadas por método.

## <a name="see-also"></a>Consulte também

- [Visão geral da animação](animation-overview.md)
- [Visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
