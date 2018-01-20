---
title: "Visão geral de storyboards"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 614b5cc4843dbb886fa9cb02c56b28452e9fae8a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="storyboards-overview"></a>Visão geral de storyboards
Este tópico mostra como usar <xref:System.Windows.Media.Animation.Storyboard> objetos para organizar e aplicar animações. Descreve como manipular interativamente <xref:System.Windows.Media.Animation.Storyboard> objetos e descreve indireta sintaxe propriedades alvo.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de animação e seus recursos básicos. Para obter uma introdução à animação, consulte a [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Você também deve saber usar propriedades anexadas. Para obter mais informações sobre as propriedades anexadas, consulte [Visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>O que é um storyboard?  
 Animações não são o único tipo útil de linha do tempo. Outras classes de linha do tempo são fornecidas para ajudá-lo a organizar conjuntos de linhas do tempo e aplicar linhas do tempo a propriedades. Cronogramas contêiner derivam o <xref:System.Windows.Media.Animation.TimelineGroup> classe e incluir <xref:System.Windows.Media.Animation.ParallelTimeline> e <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Um <xref:System.Windows.Media.Animation.Storyboard> é um tipo de cronograma contêiner que fornece informações de direcionamento para as cronogramas que ele contém. Um Storyboard pode conter qualquer tipo de <xref:System.Windows.Media.Animation.Timeline>, incluindo outros cronogramas contêiner e animações. <xref:System.Windows.Media.Animation.Storyboard>objetos permitem que você combine cronogramas que afetam uma variedade de objetos e propriedades em uma única árvore de cronograma, tornando mais fácil organizar e controlar comportamentos complexos de temporização. Por exemplo, suponha que você deseje que um botão faça estas três coisas.  
  
-   Aumenta e muda de cor quando o usuário o seleciona.  
  
-   Diminui e, em seguida, aumenta novamente para seu tamanho original quando recebe um clique.  
  
-   Diminui e esmaece até uma opacidade de 50% quando é desabilitado.  
  
 Nesse caso, você tem vários conjuntos de animações que se aplicam ao mesmo objeto e deseja que eles sejam reproduzidos em tempos diferentes, dependentes do estado do botão. <xref:System.Windows.Media.Animation.Storyboard>objetos permitem que você organize as animações e aplicá-los em grupos para um ou mais objetos.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Onde você pode usar um storyboard?  
 Um <xref:System.Windows.Media.Animation.Storyboard> pode ser usado para animar a propriedade de dependência de classes pode ser animadas (para obter mais informações sobre o que torna uma classe pode ser animada, consulte o [visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)). No entanto, como storyboarding é um recurso no nível do framework, o objeto deve pertencer ao <xref:System.Windows.NameScope> de um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
 Por exemplo, você pode usar um <xref:System.Windows.Media.Animation.Storyboard> para fazer o seguinte:  
  
-   Animar um <xref:System.Windows.Media.SolidColorBrush> (elemento não-framework) que pinta o plano de fundo de um botão (um tipo de <xref:System.Windows.FrameworkElement>),  
  
-   Animar um <xref:System.Windows.Media.SolidColorBrush> (elemento não-framework) que pinta o preenchimento de um <xref:System.Windows.Media.GeometryDrawing> (elemento não-framework) exibido usando um <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   No código, animar um <xref:System.Windows.Media.SolidColorBrush> declarado por uma classe que também contém um <xref:System.Windows.FrameworkElement>, se o <xref:System.Windows.Media.SolidColorBrush> registra seu nome com que <xref:System.Windows.FrameworkElement>.  
  
 No entanto, você não poderia usar um <xref:System.Windows.Media.Animation.Storyboard> para animar uma <xref:System.Windows.Media.SolidColorBrush> que não registrou seu nome com um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, ou não foi usado para definir uma propriedade de um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Como aplicar animações com um storyboard  
 Para usar um <xref:System.Windows.Media.Animation.Storyboard> para organizar e aplicar animações, você adiciona as animações como cronogramas filhos do <xref:System.Windows.Media.Animation.Storyboard>. O <xref:System.Windows.Media.Animation.Storyboard> classe fornece a <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> propriedades anexadas. Você pode definir essas propriedades em uma animação para especificar seu objeto de destino e sua propriedade.  
  
 Para aplicar animações a suas metas, começar o <xref:System.Windows.Media.Animation.Storyboard> usando um método ou uma ação do disparador. Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você usa um <xref:System.Windows.Media.Animation.BeginStoryboard> do objeto com um <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, ou <xref:System.Windows.DataTrigger>. No código, você também pode usar o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método.  
  
 A tabela a seguir mostra os locais diferentes onde cada <xref:System.Windows.Media.Animation.Storyboard> começar técnica é suportada: por instância, estilo, modelo de controle e modelo de dados. "Por instância" se refere à técnica de aplicar uma animação ou storyboard diretamente às instâncias de um objeto, em vez de um estilo, modelo de controle ou modelo de dados.  
  
|O storyboard é iniciado usando…|Por instância|Estilo|Modelo de controle|Modelo de dados|Exemplo|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.EventTrigger>|Sim|Sim|Sim|Sim|[Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e uma propriedade<xref:System.Windows.Trigger>|Não|Sim|Sim|Sim|[Disparar uma animação quando o valor de uma propriedade é alterado](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.DataTrigger>|Não|Sim|Sim|Sim|[Como disparar uma animação quando dados são alterados](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|Método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Sim|Não|Não|Não|[Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.Animation.Storyboard> para animar a <xref:System.Windows.FrameworkElement.Width%2A> de um <xref:System.Windows.Shapes.Rectangle> elemento e o <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usados para pintar que <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 As seções a seguir descrevem o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> propriedades anexadas em mais detalhes.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Definindo como destino elementos de estrutura, elementos de conteúdo de estrutura e congeláveis  
 Na seção anterior, mencionamos que, para uma animação encontrar seu destino, ela deve saber o nome do destino e a propriedade a ser animada. Especifica a propriedade para animar é muito simples: basta definir <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> com o nome da propriedade para animar.  Especifique o nome do objeto cuja propriedade para animar definindo o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> propriedade na animação.  
  
 Para o <xref:System.Windows.Setter.TargetName%2A> propriedade funcione, o objeto de destino deve ter um nome. Atribuir um nome para um <xref:System.Windows.FrameworkElement> ou um <xref:System.Windows.FrameworkContentElement> na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é diferente de atribuir um nome para um <xref:System.Windows.Freezable> objeto.  
  
 Elementos de estrutura são as classes que herdam o <xref:System.Windows.FrameworkElement> classe. Exemplos de elementos do framework <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, e <xref:System.Windows.Shapes.Rectangle>. Basicamente, todas as janelas, todos os painéis e todos os controles são elementos. Elementos de conteúdo do Framework são as classes que herdam o <xref:System.Windows.FrameworkContentElement> classe. Exemplos de elementos de conteúdo do framework <xref:System.Windows.Documents.FlowDocument> e <xref:System.Windows.Documents.Paragraph>. Se você não tiver certeza se um tipo é um elemento de estrutura ou um elemento de conteúdo de estrutura, verifique se ele tem uma propriedade Name. Se isso acontecer, provavelmente, ele será um elemento de estrutura ou um elemento de conteúdo de estrutura. Para ter certeza, confira a seção Hierarquia de herança da página de seu tipo.  
  
 Para habilitar o direcionamento de um elemento do framework ou um elemento de conteúdo do framework em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você definir sua <xref:System.Windows.FrameworkElement.Name%2A> propriedade. No código, você também precisa usar o <xref:System.Windows.NameScope.RegisterName%2A> método para registrar o nome do elemento com o elemento para o qual você criou um <xref:System.Windows.NameScope>.  
  
 O exemplo a seguir, retirado do exemplo anterior, atribui o nome `MyRectangle` um <xref:System.Windows.Shapes.Rectangle>, um tipo de <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Depois que ele tiver um nome, você poderá animar uma propriedade desse elemento.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable>os tipos são as classes que herdam o <xref:System.Windows.Freezable> classe. Exemplos de <xref:System.Windows.Freezable> incluem <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, e <xref:System.Windows.Media.GradientStop>.  
  
 Para habilitar o direcionamento de uma <xref:System.Windows.Freezable> uma animação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você usa o [diretiva X:Name](../../../../docs/framework/xaml-services/x-name-directive.md) para atribuir um nome. No código, você deve usar o <xref:System.Windows.NameScope.RegisterName%2A> método para registrar o nome do elemento para o qual você criou um <xref:System.Windows.NameScope>.  
  
 O exemplo a seguir atribui um nome para um <xref:System.Windows.Freezable> objeto.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 Em seguida, o objeto pode ser o destino de uma animação.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard>objetos usam escopos de nome para resolver o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriedade. Para obter mais informações sobre escopos de nome no WPF, consulte [Escopos de nome XAML no WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md). Se o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriedade for omitida, a animação atinge o elemento no qual ela está definida, ou, no caso de estilos, o elemento de estilo.  
  
 Às vezes, um nome não pode ser atribuído a um <xref:System.Windows.Freezable> objeto. Por exemplo, se um <xref:System.Windows.Freezable> é declarado como um recurso ou usado para definir um valor de propriedade em um estilo, não pode ser dado um nome. Como ele não tem um nome, ele não pode ser definido como destino diretamente – mas ele pode ser definido como destino indiretamente. As próximas seções descrevem como usar o direcionamento indireto.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Direcionamento indireto  
 Há vezes uma <xref:System.Windows.Freezable> não pode ser alvo diretamente de uma animação, como quando o <xref:System.Windows.Freezable> é declarado como um recurso ou usado para definir um valor de propriedade em um estilo. Nesses casos, mesmo que você não pode direcionar diretamente, você ainda pode animar o <xref:System.Windows.Freezable> objeto. Em vez de configuração o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriedade com o nome do <xref:System.Windows.Freezable>, você dê a ele o nome do elemento ao qual o <xref:System.Windows.Freezable> "pertence." Por exemplo, um <xref:System.Windows.Media.SolidColorBrush> usado para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> de um retângulo elemento pertence a esse retângulo. Para animar o pincel, você poderia definir a animação <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> com uma cadeia de propriedades que começa na propriedade do elemento do framework ou elemento de conteúdo do framework o <xref:System.Windows.Freezable> foi usado para definir e termina com o <xref:System.Windows.Freezable> propriedade a ser animada.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Observe que, se o <xref:System.Windows.Freezable> está congelado, um clone será feito e este clone será animado. Quando isso acontece, o objeto original <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> propriedade continua a retornar `false`, porque o objeto original não é realmente animado. Para obter mais informações sobre clonagem, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Observe também que, ao usar o direcionamento indireto de propriedade, é possível definir como destino objetos inexistentes. Por exemplo, você pode assumir que o <xref:System.Windows.Controls.Control.Background%2A> de um determinado botão foi definido com um <xref:System.Windows.Media.SolidColorBrush> e tentar animar sua cor, quando na verdade um <xref:System.Windows.Media.LinearGradientBrush> foi usado para definir o plano de fundo do botão. Nesses casos, nenhuma exceção é lançada; a animação não tem um efeito visível porque <xref:System.Windows.Media.LinearGradientBrush> não reage a alterações de <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriedade.  
  
 As próximas seções descrevem a sintaxe de direcionamento indireto de propriedade mais detalhadamente.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Definindo indiretamente como destino uma propriedade de um congelável em XAML  
 Para selecionar uma propriedade de um freezable em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use a seguinte sintaxe.  
  
||  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName* é a propriedade do <xref:System.Windows.FrameworkElement> que o <xref:System.Windows.Freezable> é usado para definir, e  
  
-   *FreezablePropertyName* é a propriedade do <xref:System.Windows.Freezable> para animar.  
  
 O código a seguir mostra como animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para definir o  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A>de um elemento de retângulo.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 Às vezes, você precisa ter como destino um congelável contido em uma coleção ou matriz.  
  
 Para definir um congelável como destino contido em uma coleção, use a sintaxe de caminho a seguir.  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Onde *CollectionIndex* é o índice do objeto em sua matriz ou coleção.  
  
 Por exemplo, suponha que um retângulo possui um <xref:System.Windows.Media.TransformGroup> recurso aplicado à sua <xref:System.Windows.UIElement.RenderTransform%2A> propriedade e você deseja animar uma das transformações que ele contém.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 O código a seguir mostra como animar a <xref:System.Windows.Media.RotateTransform.Angle%2A> propriedade o <xref:System.Windows.Media.RotateTransform> mostrado no exemplo anterior.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Definindo indiretamente como destino uma propriedade de um congelável no código  
 No código, você cria um <xref:System.Windows.PropertyPath> objeto. Quando você cria o <xref:System.Windows.PropertyPath>, você especificar um <xref:System.Windows.PropertyPath.Path%2A> e <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Para criar <xref:System.Windows.PropertyPath.PathParameters%2A>, você cria uma matriz do tipo <xref:System.Windows.DependencyProperty> que contém uma lista de campos de identificador de propriedade de dependência. É o primeiro campo de identificador para a propriedade do <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> que o <xref:System.Windows.Freezable> é usado para definir. O próximo campo identificador representa a propriedade do <xref:System.Windows.Freezable> ao destino. Pense nisso como uma cadeia de propriedades que se conecta a <xref:System.Windows.Freezable> para o <xref:System.Windows.FrameworkElement> objeto.  
  
 A seguir está um exemplo de uma cadeia de propriedade de dependência que tem como alvo o <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> de um elemento de retângulo.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Você também precisa especificar um <xref:System.Windows.PropertyPath.Path%2A>. Um <xref:System.Windows.PropertyPath.Path%2A> é um <xref:System.String> que informa o <xref:System.Windows.PropertyPath.Path%2A> como interpretar seus <xref:System.Windows.PropertyPath.PathParameters%2A>. Ele usa a sintaxe a seguir.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex* é o índice do <xref:System.Windows.DependencyProperty> matriz que contém o identificador do <xref:System.Windows.FrameworkElement> propriedade do objeto que o <xref:System.Windows.Freezable> é usado para definir, e  
  
-   *FreezablePropertyArrayIndex* é o índice da <xref:System.Windows.DependencyProperty> matriz que contém o identificador de propriedade de destino.  
  
 A exemplo a seguir mostra o <xref:System.Windows.PropertyPath.Path%2A> que seria acompanham o <xref:System.Windows.PropertyPath.PathParameters%2A> definida no exemplo anterior.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 O exemplo a seguir combina o código nos exemplos anteriores para animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> de um elemento de retângulo.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Às vezes, você precisa ter como destino um congelável contido em uma coleção ou matriz. Por exemplo, suponha que um retângulo possui um <xref:System.Windows.Media.TransformGroup> recurso aplicado à sua <xref:System.Windows.UIElement.RenderTransform%2A> propriedade e você deseja animar uma das transformações que ele contém.  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Destino um <xref:System.Windows.Freezable> contido em uma coleção, você use a seguinte sintaxe de caminho.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 Onde *CollectionIndex* é o índice do objeto em sua matriz ou coleção.  
  
 Destino de <xref:System.Windows.Media.RotateTransform.Angle%2A> propriedade do <xref:System.Windows.Media.RotateTransform>, a segunda transformação no <xref:System.Windows.Media.TransformGroup>, você usaria o seguinte <xref:System.Windows.PropertyPath.Path%2A> e <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 O exemplo a seguir mostra o código completo para animar a <xref:System.Windows.Media.RotateTransform.Angle%2A> de um <xref:System.Windows.Media.RotateTransform> contido em um <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Definindo indiretamente como destino um congelável como o ponto de partida  
 As seções anteriores descreveram como destino indiretamente uma <xref:System.Windows.Freezable> iniciando com um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> e criando uma cadeia de propriedade para um <xref:System.Windows.Freezable> subpropriedade. Você também pode usar um <xref:System.Windows.Freezable> como um valor inicial de ponto e indiretamente visar uma das suas <xref:System.Windows.Freezable> subpropriedades. Uma restrição adicional se aplica ao usar um <xref:System.Windows.Freezable> como ponto de partida para definição de alvo indireta: inicial <xref:System.Windows.Freezable> e cada <xref:System.Windows.Freezable> entre ele e o subtipo indiretamente destino deve ser não-congelados.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Controlando um storyboard de forma interativa no XAML  
 Para iniciar um storyboard no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você usa um <xref:System.Windows.Media.Animation.BeginStoryboard> disparar a ação. <xref:System.Windows.Media.Animation.BeginStoryboard>distribui as animações aos objetos e propriedades que ele anima e inicia o storyboard. (Para obter detalhes sobre esse processo, consulte o [visão geral do sistema de controle de tempo e animação](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).) Se você fornecer o <xref:System.Windows.Media.Animation.BeginStoryboard> especificando um nome de seu <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> propriedade, você torná-lo um storyboard controlável. Você poderá então controlar o storyboard de forma interativa depois que ele for iniciado. Veja a seguir uma lista de ações de storyboard controlável usadas com gatilhos de evento para controlar um storyboard.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Altera a velocidade do storyboard.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avança um storyboard até o final do período de preenchimento, se ele tiver um.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Para o storyboard.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>Remove o storyboard.  
  
 No exemplo a seguir, as ações de storyboard controlável são usadas para controlar um storyboard de forma interativa.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Controlando um storyboard de forma interativa usando um código  
 Os exemplos anteriores mostraram como animar usando ações de gatilho. No código, você também pode controlar um storyboard usando métodos interativos do <xref:System.Windows.Media.Animation.Storyboard> classe. Para uma <xref:System.Windows.Media.Animation.Storyboard> ser tornado interativo em código, você deve usar a sobrecarga apropriada do storyboard <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método e especifique `true` para torná-lo controlável. Consulte o <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> para obter mais informações.  
  
 A lista a seguir mostra os métodos que podem ser usados para manipular um <xref:System.Windows.Media.Animation.Storyboard> depois de iniciada:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 A vantagem de usar esses métodos é que você não precisa criar <xref:System.Windows.Trigger> ou <xref:System.Windows.TriggerAction> objetos, você precisa apenas uma referência a controlável <xref:System.Windows.Media.Animation.Storyboard> você deseja manipular.  
  
 **Observação:** todas as ações interativas executadas em um <xref:System.Windows.Media.Animation.Clock>e, portanto, também em um <xref:System.Windows.Media.Animation.Storyboard> ocorrerá no próximo tick do mecanismo de tempo que irá acontecer logo antes da próxima renderização. Por exemplo, se você usar o <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método para saltar para outro ponto de uma animação, o valor da propriedade não é alterado imediatamente, em vez disso, o valor é alterado no próximo tick do mecanismo de temporização.  
  
 O exemplo a seguir mostra como aplicar e controlar animações usando os métodos interativos do <xref:System.Windows.Media.Animation.Storyboard> classe.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Animar em um estilo  
 Você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para definir animações em um <xref:System.Windows.Style>. Animação com um <xref:System.Windows.Media.Animation.Storyboard> em uma <xref:System.Windows.Style> é semelhante ao uso de um <xref:System.Windows.Media.Animation.Storyboard> em outro lugar, com as seguintes três exceções:  
  
-   Você não especificar um <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; o <xref:System.Windows.Media.Animation.Storyboard> sempre tem como alvo o elemento ao qual o <xref:System.Windows.Style> é aplicada. Destino <xref:System.Windows.Freezable> objetos, você deve usar um direcionamento indireta. Para obter mais informações sobre definição de alvo indireta, consulte o [direcionamento indireta](#pathsyntaxforchangeable) seção.  
  
-   Não é possível especificar um <xref:System.Windows.EventTrigger.SourceName%2A> para um <xref:System.Windows.EventTrigger> ou <xref:System.Windows.Trigger>.  
  
-   Você não pode usar expressões de associação de dados ou referências de recurso dinâmico para definir <xref:System.Windows.Media.Animation.Storyboard> ou valores de propriedade de animação. Isso ocorre porque tudo dentro de um <xref:System.Windows.Style> deve ser thread-safe, e o sistema de controle de tempo deve <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objetos para torná-los thread-safe. Um <xref:System.Windows.Media.Animation.Storyboard> não pode ser congelado se ele ou seus cronogramas filhos contiverem expressões de associação de dados ou referências de recurso dinâmico. Para obter mais informações sobre congelamento e outros <xref:System.Windows.Freezable> recursos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você não pode declarar manipuladores de eventos para <xref:System.Windows.Media.Animation.Storyboard> ou eventos de animação.  
  
 Para obter um exemplo mostrando como definir um storyboard em um estilo, consulte o [animar em um estilo](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md) exemplo.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>Animar em um ControlTemplate  
 Você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para definir animações em um <xref:System.Windows.Controls.ControlTemplate>. Animação com um <xref:System.Windows.Media.Animation.Storyboard> em uma <xref:System.Windows.Controls.ControlTemplate> é semelhante ao uso de um <xref:System.Windows.Media.Animation.Storyboard> em outro lugar, com as seguintes duas exceções:  
  
-   O <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> somente pode se referir a objetos filho de <xref:System.Windows.Controls.ControlTemplate>. Se <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> não for especificado, a animação atinge o elemento ao qual o <xref:System.Windows.Controls.ControlTemplate> é aplicada.  
  
-   O <xref:System.Windows.EventTrigger.SourceName%2A> para um <xref:System.Windows.EventTrigger> ou um <xref:System.Windows.Trigger> somente pode se referir a objetos filho de <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Você não pode usar expressões de associação de dados ou referências de recurso dinâmico para definir <xref:System.Windows.Media.Animation.Storyboard> ou valores de propriedade de animação. Isso ocorre porque tudo dentro de um <xref:System.Windows.Controls.ControlTemplate> deve ser thread-safe, e o sistema de controle de tempo deve <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objetos para torná-los thread-safe. Um <xref:System.Windows.Media.Animation.Storyboard> não pode ser congelado se ele ou seus cronogramas filhos contiverem expressões de associação de dados ou referências de recurso dinâmico. Para obter mais informações sobre congelamento e outros <xref:System.Windows.Freezable> recursos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você não pode declarar manipuladores de eventos para <xref:System.Windows.Media.Animation.Storyboard> ou eventos de animação.  
  
 Para obter um exemplo mostrando como definir um storyboard em um <xref:System.Windows.Controls.ControlTemplate>, consulte o [animar em um ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md) exemplo.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Animar quando um valor da propriedade é alterado  
 Em estilos e modelos de controle, você pode usar objetos Trigger para iniciar um storyboard quando uma propriedade é alterada. Para obter exemplos, consulte [disparar uma animação quando um valor de alterações de propriedade](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) e [animar em um ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Animações aplicadas pela propriedade <xref:System.Windows.Trigger> objetos se comportam de maneira mais complexa que <xref:System.Windows.EventTrigger> animações ou animações iniciadas usando <xref:System.Windows.Media.Animation.Storyboard> métodos.  Elas "entregam" animações definida por outros <xref:System.Windows.Trigger> objetos, mas se compõem com <xref:System.Windows.EventTrigger> e animações acionadas por método.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
