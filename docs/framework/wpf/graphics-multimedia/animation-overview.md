---
title: Visão geral da animação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: 870fc1d1f02dca7d4488a27385fcfeaec8098ced
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039183"
---
# <a name="animation-overview"></a>Visão geral da animação

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um conjunto poderoso de recursos gráficos e de layout que permitem criar interfaces de usuário atraentes e documentos atraentes. A animação pode tornar uma interface do usuário ainda mais espetacular e utilizável. Apenas animando uma cor de plano de fundo ou aplicando uma <xref:System.Windows.Media.Transform>animada, você pode criar transições de tela dramáticas ou fornecer indicações visuais úteis.

Esta visão geral fornece uma introdução à animação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e ao sistema de tempo. Ele se concentra na animação de objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando storyboards.

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>Introdução a animações

A animação é uma ilusão criada passando-se rapidamente por uma série de imagens, cada uma ligeiramente diferente da anterior. O cérebro vê a sequência de imagens como uma única cena em mudança. Em filmes, essa ilusão é criada usando câmeras que gravam várias fotografias, ou quadros, a cada segundo. Quando os quadros são executados por um projetor, o público-alvo vê um filme animado.

A animação em um computador é semelhante. Por exemplo, um programa que cria um desenho de um retângulo que desaparece pode funcionar conforme descrito a seguir.

- O programa cria um temporizador.

- O programa verifica o temporizador em intervalos definidos para ver quanto tempo transcorreu.

- Cada vez que o programa verifica o temporizador, ele calcula o valor de opacidade atual para o retângulo com base em quanto tempo transcorreu.

- O programa então atualiza o retângulo com o novo valor e o redesenha.

Antes da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os desenvolvedores do Microsoft Windows tinham que criar e gerenciar seus próprios sistemas de tempo ou usar bibliotecas personalizadas especiais. a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui um sistema de tempo eficiente que é exposto por meio de código gerenciado e [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e que está profundamente integrado à estrutura de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A animação do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] facilita a animação de controles e outros objetos gráficos.

O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realiza todo o trabalho nos bastidores para gerenciar um sistema de temporização e redesenhar a tela de modo eficiente. Ele fornece classes de temporização que permitem que você se concentre nos efeitos que deseja criar, em vez de precisar concentrar-se na mecânica envolvida para atingir tais efeitos. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também torna fácil criar sua própria animação expondo classes de animação base das quais suas classes podem herdar, para assim produzir animações personalizadas. Essas animações personalizadas obtêm muitos dos benefícios de desempenho das classes de animação padrão.

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>Sistema de Animação de Propriedades do WPF

Se você entender alguns conceitos importantes sobre o sistema de tempo, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animações podem ser mais fáceis de usar. O mais importante é que, em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você anima objetos aplicando animação às suas propriedades individuais. Por exemplo, para que um elemento de estrutura cresça, você anima suas <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> Propriedades. Para fazer um objeto desaparecer da exibição, você anima sua propriedade <xref:System.Windows.UIElement.Opacity%2A>.

Para uma propriedade ter capacidade de animação, ela deve atender aos três requisitos a seguir:

- Ela deve ser uma propriedade de dependência.

- Ele deve pertencer a uma classe que herda de <xref:System.Windows.DependencyObject> e implementa a interface <xref:System.Windows.Media.Animation.IAnimatable>.

- Deve haver um tipo de animação compatível disponível. (Se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não fornecer um, você poderá criar o seu próprio. Consulte a [visão geral das animações personalizadas](custom-animations-overview.md).)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contém muitos objetos que têm <xref:System.Windows.Media.Animation.IAnimatable> Propriedades. Controles como <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.TabControl>, além de <xref:System.Windows.Controls.Panel> e <xref:System.Windows.Shapes.Shape> objetos herdam de <xref:System.Windows.DependencyObject>. A maioria de suas propriedades são propriedades de dependência.

Você pode usar animações em quase qualquer lugar, o que inclui em estilos e modelos de controle. Animações não precisam ser visuais; você pode animar objetos que não fazem parte da interface do usuário se eles atendem aos critérios descritos nesta seção.

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Exemplo: fazer com que um elemento apareça e desapareça da exibição

Este exemplo mostra como usar uma animação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para animar o valor de uma propriedade de dependência. Ele usa um <xref:System.Windows.Media.Animation.DoubleAnimation>, que é um tipo de animação que gera valores de <xref:System.Double>, para animar a propriedade <xref:System.Windows.UIElement.Opacity%2A> de um <xref:System.Windows.Shapes.Rectangle>. Como resultado, o <xref:System.Windows.Shapes.Rectangle> esmaece e sai da exibição.

A primeira parte do exemplo cria um elemento <xref:System.Windows.Shapes.Rectangle>. As etapas a seguir mostram como criar uma animação e aplicá-la à propriedade <xref:System.Windows.UIElement.Opacity%2A> do retângulo.

O seguinte mostra como criar um elemento <xref:System.Windows.Shapes.Rectangle> em um <xref:System.Windows.Controls.StackPanel> em XAML.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

O seguinte mostra como criar um elemento <xref:System.Windows.Shapes.Rectangle> em um <xref:System.Windows.Controls.StackPanel> no código.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>Parte 1: criar uma DoubleAnimation

Uma maneira de fazer com que um elemento fique esmaecido e fora do modo de exibição é animar sua propriedade <xref:System.Windows.UIElement.Opacity%2A>. Como a propriedade <xref:System.Windows.UIElement.Opacity%2A> é do tipo <xref:System.Double>, você precisa de uma animação que produza valores duplos. Uma <xref:System.Windows.Media.Animation.DoubleAnimation> é uma dessas animações. Uma <xref:System.Windows.Media.Animation.DoubleAnimation> cria uma transição entre dois valores duplos. Para especificar seu valor inicial, defina sua propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. Para especificar seu valor final, defina sua propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.

1. Um valor de opacidade de `1.0` torna o objeto completamente opaco e um valor de opacidade de `0.0` o torna totalmente invisível. Para fazer a transição de animação de `1.0` para `0.0` defina sua propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> como `1.0` e sua propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> como `0.0`. O seguinte mostra como criar um <xref:System.Windows.Media.Animation.DoubleAnimation> em XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    O seguinte mostra como criar um <xref:System.Windows.Media.Animation.DoubleAnimation> no código.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. Em seguida, você deve especificar um <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. A <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma animação especifica quanto tempo leva para ir do seu valor inicial para seu valor de destino. O seguinte mostra como definir a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> para cinco segundos em XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    Veja a seguir como definir o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> como cinco segundos no código.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. O código anterior mostrou uma animação que muda de `1.0` para `0.0`, o que faz com que o elemento de destino fique esmaecido de completamente opaco para totalmente invisível. Para fazer com que o elemento volte a ser exibido depois que ele desaparecer, defina a propriedade <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> da animação como `true`. Para fazer a animação repetir indefinidamente, defina sua propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> como <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. O seguinte mostra como definir as propriedades <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> e <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> em XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    O seguinte mostra como definir as propriedades <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> e <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> no código.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>Parte 2: criar um storyboard

Para aplicar uma animação a um objeto, você cria um <xref:System.Windows.Media.Animation.Storyboard> e usa as propriedades <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> anexadas para especificar o objeto e a propriedade a serem animados.

1. Crie o <xref:System.Windows.Media.Animation.Storyboard> e adicione a animação como seu filho. O seguinte mostra como criar o <xref:System.Windows.Media.Animation.Storyboard> em XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    Para criar o <xref:System.Windows.Media.Animation.Storyboard> no código, declare uma variável <xref:System.Windows.Media.Animation.Storyboard> no nível de classe.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    Em seguida, inicialize o <xref:System.Windows.Media.Animation.Storyboard> e adicione a animação como seu filho.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. O <xref:System.Windows.Media.Animation.Storyboard> precisa saber onde aplicar a animação. Use a propriedade <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> anexada para especificar o objeto a ser animado. O seguinte mostra como definir o nome de destino do <xref:System.Windows.Media.Animation.DoubleAnimation> como `MyRectangle` em XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    O seguinte mostra como definir o nome de destino do <xref:System.Windows.Media.Animation.DoubleAnimation> como `MyRectangle` no código.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. Use a propriedade <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> anexada para especificar a propriedade a ser animada. O seguinte mostra como a animação é configurada para direcionar a propriedade <xref:System.Windows.UIElement.Opacity%2A> do <xref:System.Windows.Shapes.Rectangle> em XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    O seguinte mostra como a animação é configurada para direcionar a propriedade <xref:System.Windows.UIElement.Opacity%2A> do <xref:System.Windows.Shapes.Rectangle> no código.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

Para obter mais informações sobre a sintaxe de <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> e exemplos adicionais, consulte a [visão geral de storyboards](storyboards-overview.md).

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Parte 3 (XAML): associar o storyboard com um gatilho

A maneira mais fácil de aplicar e iniciar uma <xref:System.Windows.Media.Animation.Storyboard> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é usar um gatilho de evento. Esta seção mostra como associar o <xref:System.Windows.Media.Animation.Storyboard> a um gatilho em XAML.

1. Crie um objeto <xref:System.Windows.Media.Animation.BeginStoryboard> e associe o storyboard a ele. Um <xref:System.Windows.Media.Animation.BeginStoryboard> é um tipo de <xref:System.Windows.TriggerAction> que se aplica e inicia uma <xref:System.Windows.Media.Animation.Storyboard>.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. Crie um <xref:System.Windows.EventTrigger> e adicione o <xref:System.Windows.Media.Animation.BeginStoryboard> à sua coleção de <xref:System.Windows.EventTrigger.Actions%2A>. Defina a propriedade <xref:System.Windows.EventTrigger.RoutedEvent%2A> do <xref:System.Windows.EventTrigger> para o evento roteado que você deseja iniciar o <xref:System.Windows.Media.Animation.Storyboard>. (Para obter mais informações sobre eventos roteados, consulte a [visão geral de eventos roteados](../advanced/routed-events-overview.md).)

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. Adicione o <xref:System.Windows.EventTrigger> à coleção de <xref:System.Windows.FrameworkElement.Triggers%2A> do retângulo.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Parte 3 (código): associar o storyboard com um manipulador de eventos

A maneira mais fácil de aplicar e iniciar um <xref:System.Windows.Media.Animation.Storyboard> no código é usar um manipulador de eventos. Esta seção mostra como associar o <xref:System.Windows.Media.Animation.Storyboard> a um manipulador de eventos no código.

1. Registre-se para o evento <xref:System.Windows.FrameworkElement.Loaded> do retângulo.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. Declare o manipulador de eventos. No manipulador de eventos, use o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> para aplicar o storyboard.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]

### <a name="complete-example"></a>Exemplo completo

O seguinte mostra como criar um retângulo que esmaece e sai da exibição em XAML.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]

O exemplo a seguir mostra como criar um retângulo que aparece e desaparece de exibição no código.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]

<a name="animationtypes"></a>

## <a name="animation-types"></a>Tipos de animação

Já que as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade que usa um <xref:System.Double>, como a propriedade <xref:System.Windows.FrameworkElement.Width%2A> de um elemento, use uma animação que produza valores de <xref:System.Double>. Para animar uma propriedade que usa um <xref:System.Windows.Point>, use uma animação que produz <xref:System.Windows.Point> valores, e assim por diante. Devido ao número de diferentes tipos de propriedade, há várias classes de animação no namespace <xref:System.Windows.Media.Animation>. Felizmente, elas seguem uma convenção de nomenclatura estrita que facilita a diferenciação entre elas:

- *tipo*de \<> animação

  Conhecida como "de/para/por" ou animação "básica", ela anima entre um valor inicial e outro de destino, ou então pela adição de um valor de deslocamento ao seu valor inicial.

  - Para especificar um valor inicial, defina a propriedade De da animação.

  - Para especificar um valor final, defina a propriedade Para da animação.

  - Para especificar um valor de deslocamento, defina a propriedade Por da animação.

  Os exemplos nesta visão geral usam essas animações porque elas são mais simples de usar. As animações de/para/por são descritas em detalhes na visão geral das animações de/para/por.

- \<*Type*>AnimationUsingKeyFrames

  Animações de quadro chave são mais avançadas que animações de/para/por porque você pode especificar qualquer número de valores de destino e até mesmo controlar seu método de interpolação. Alguns tipos só podem ser animados com animações de quadro chave. As animações de quadro-chave são descritas em detalhes na [visão geral das animações de quadro chave](key-frame-animations-overview.md).

- *tipo*de \<> AnimationUsingPath

  Animações de caminho permitem que você use um caminho geométrico para produzir valores animados.

- *tipo*de \<> AnimationBase

  Classe abstrata que, quando você a implementa, anima um *tipo*de \<> valor. Essa classe serve como a classe base para \<*tipo*> animação e \<*tipo*> classes AnimationUsingKeyFrames. Você só precisará lidar diretamente com essas classes se quiser criar suas próprias animações personalizadas. Caso contrário, use um *tipo*de \<> animação ou quadro-chave\<*tipo*> animação.

Na maioria dos casos, você desejará usar o *tipo*de \<> classes de animação, como <xref:System.Windows.Media.Animation.DoubleAnimation> e <xref:System.Windows.Media.Animation.ColorAnimation>.

A tabela a seguir mostra vários tipos de animação comuns e algumas propriedades com as qual eles são usados.

|Tipo de propriedade|Animação básica (De/Para/Por) correspondente|Animação de quadro chave correspondente|Animação de caminho correspondente|Exemplo de uso|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Nenhum|Anime a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> ou um <xref:System.Windows.Media.GradientStop>.|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Anime a <xref:System.Windows.FrameworkElement.Width%2A> de um <xref:System.Windows.Controls.DockPanel> ou a <xref:System.Windows.FrameworkElement.Height%2A> de um <xref:System.Windows.Controls.Button>.|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Anime a posição de <xref:System.Windows.Media.EllipseGeometry.Center%2A> de um <xref:System.Windows.Media.EllipseGeometry>.|
|<xref:System.String>|Nenhum|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Nenhum|Anime a <xref:System.Windows.Controls.TextBlock.Text%2A> de um <xref:System.Windows.Controls.TextBlock> ou a <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.Button>.|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>As animações são linhas do tempo

Todos os tipos de animação herdam da classe <xref:System.Windows.Media.Animation.Timeline>; Portanto, todas as animações são tipos especializados de linhas do tempo. Um <xref:System.Windows.Media.Animation.Timeline> define um segmento de tempo. Você pode especificar os *comportamentos de tempo* de uma linha do tempo: sua <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, quantas vezes ela é repetida e até mesmo quão rápido é o andamento.

Como uma animação é uma <xref:System.Windows.Media.Animation.Timeline>, ela também representa um segmento de tempo. Uma animação também calcula valores de saída conforme eles avançam por seu segmento especificado de tempo (ou <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Conforme a animação progride ou é "reproduzida", ela atualiza a propriedade com a qual está associada.

Três propriedades de tempo usadas com frequência são <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>e <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.

#### <a name="the-duration-property"></a>A propriedade Duration

Conforme mencionado anteriormente, uma linha do tempo representa um segmento de tempo. O comprimento desse segmento é determinado pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A> da linha do tempo, que geralmente é especificado usando um valor de <xref:System.Windows.Duration.TimeSpan%2A>. Quando uma linha do tempo atinge o final de sua duração, ela completou uma iteração.

Uma animação usa sua propriedade <xref:System.Windows.Media.Animation.Timeline.Duration%2A> para determinar seu valor atual. Se você não especificar um valor <xref:System.Windows.Media.Animation.Timeline.Duration%2A> para uma animação, ele usará 1 segundo, que é o padrão.

A sintaxe a seguir mostra uma versão simplificada da sintaxe do atributo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para a propriedade <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.

*horas* `:` *minutos* `:` *segundos*

A tabela a seguir mostra várias configurações de <xref:System.Windows.Duration> e seus valores resultantes.

|Configuração|Valor resultante|
|-------------|---------------------|
|0:0:5.5|5,5 segundos.|
|0:30:5.5|30 minutos e 5,5 segundos.|
|1:30:5.5|1 hora, 30 minutos e 5,5 segundos.|

Uma maneira de especificar um <xref:System.Windows.Duration> no código é usar o método <xref:System.TimeSpan.FromSeconds%2A> para criar uma <xref:System.TimeSpan>e, em seguida, declarar uma nova estrutura de <xref:System.Windows.Duration> usando essa <xref:System.TimeSpan>.

Para obter mais informações sobre valores de <xref:System.Windows.Duration> e a sintaxe de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] completa, consulte a estrutura de <xref:System.Windows.Duration>.

#### <a name="autoreverse"></a>AutoReverse

A propriedade <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> especifica se uma linha do tempo é reproduzida após atingir o final de seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Se você definir essa propriedade de animação como `true`, uma animação será invertida depois que atingir o final de seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, jogando de seu valor final de volta ao seu valor inicial. Por padrão, essa propriedade é `false`.

#### <a name="repeatbehavior"></a>RepeatBehavior

A propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> especifica quantas vezes uma linha de tempo é reproduzida. Por padrão, as linhas do tempo têm uma contagem de iteração de `1.0`, o que significa que elas são executadas uma vez e não se repetem.

Para obter mais informações sobre essas propriedades e outras, consulte a [visão geral de comportamentos de tempo](timing-behaviors-overview.md).

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>Aplicar uma animação a uma propriedade

As seções anteriores descrevem os diferentes tipos de animações e suas propriedades de temporização. Esta seção mostra como aplicar a animação à propriedade que você deseja animar. <xref:System.Windows.Media.Animation.Storyboard> objetos fornecem uma maneira de aplicar animações a propriedades. Uma <xref:System.Windows.Media.Animation.Storyboard> é uma *linha do tempo de contêiner* que fornece informações de destino para as animações que ele contém.

### <a name="targeting-objects-and-properties"></a>Usar objetos e propriedades como destino

A classe <xref:System.Windows.Media.Animation.Storyboard> fornece as propriedades <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> anexadas. Ao definir essas propriedades em uma animação, você diz à animação o que animar. No entanto, antes de uma animação poder usar um objeto como destino, normalmente esse objeto deverá receber um nome.

Atribuir um nome a um <xref:System.Windows.FrameworkElement> difere da atribuição de um nome a um objeto <xref:System.Windows.Freezable>. A maioria dos controles e painéis são elementos framework; no entanto, a maioria dos objetos puramente gráficos como pincéis, transformações e geometrias são objetos congeláveis. Se você não tiver certeza se um tipo é um <xref:System.Windows.FrameworkElement> ou um <xref:System.Windows.Freezable>, consulte a seção **hierarquia de herança** de sua documentação de referência.

- Para fazer uma <xref:System.Windows.FrameworkElement> um destino de animação, você dá um nome definindo sua propriedade <xref:System.Windows.FrameworkElement.Name%2A>. No código, você também deve usar o método <xref:System.Windows.FrameworkElement.RegisterName%2A> para registrar o nome do elemento com a página à qual ele pertence.

- Para tornar um objeto de <xref:System.Windows.Freezable> um destino de animação no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use a [diretiva x:Name](../../xaml-services/x-name-directive.md) para atribuir um nome a ele. No código, basta usar o método <xref:System.Windows.FrameworkElement.RegisterName%2A> para registrar o objeto com a página à qual ele pertence.

As seções a seguir fornecem um exemplo de nomear um elemento em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e código. Para obter informações mais detalhadas sobre nomenclatura e direcionamento, consulte a [visão geral dos storyboards](storyboards-overview.md).

### <a name="applying-and-starting-storyboards"></a>Aplicar e iniciar Storyboards

Para iniciar um storyboard em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você o associa a um <xref:System.Windows.EventTrigger>. Um <xref:System.Windows.EventTrigger> é um objeto que descreve as ações a serem executadas quando um evento especificado ocorrer. Uma dessas ações pode ser uma ação <xref:System.Windows.Media.Animation.BeginStoryboard>, que você usa para iniciar o storyboard. Gatilhos de evento são semelhantes ao conceito de manipuladores de eventos porque eles permitem que você especifique como o aplicativo responde a um evento específico. Ao contrário dos manipuladores de eventos, os gatilhos de evento podem ser totalmente descritos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; nenhum outro código é necessário.

Para iniciar um <xref:System.Windows.Media.Animation.Storyboard> no código, você pode usar um <xref:System.Windows.EventTrigger> ou usar o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> da classe <xref:System.Windows.Media.Animation.Storyboard>.

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>Controlar interativamente um storyboard

O exemplo anterior mostrou como iniciar um <xref:System.Windows.Media.Animation.Storyboard> quando ocorre um evento. Você também pode controlar interativamente um <xref:System.Windows.Media.Animation.Storyboard> depois que ele é iniciado: você pode pausar, retomar, parar, avançar até seu período de preenchimento, buscar e remover o <xref:System.Windows.Media.Animation.Storyboard>. Para obter mais informações e um exemplo que mostra como controlar interativamente um <xref:System.Windows.Media.Animation.Storyboard>, consulte a [visão geral de storyboards](storyboards-overview.md).

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>O que acontece após o término da animação?

A propriedade <xref:System.Windows.Media.Animation.FillBehavior> especifica como uma linha do tempo se comporta quando termina. Por padrão, uma linha do tempo começa <xref:System.Windows.Media.Animation.ClockState.Filling> quando termina. Uma animação <xref:System.Windows.Media.Animation.ClockState.Filling> mantém seu valor final de saída.

O <xref:System.Windows.Media.Animation.DoubleAnimation> no exemplo anterior não termina porque sua propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> está definida como <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. O exemplo a seguir anima um retângulo usando uma animação similar. Ao contrário do exemplo anterior, as propriedades <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> e <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> dessa animação são deixadas com seus valores padrão. Portanto, a animação avança de 1 para 0 durante cinco segundos e, em seguida, é interrompida.

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

Como seu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> não foi alterado de seu valor padrão, que é <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, a animação mantém seu valor final, 0, quando termina. Portanto, a <xref:System.Windows.UIElement.Opacity%2A> do retângulo permanece em 0 após o término da animação. Se você definir o <xref:System.Windows.UIElement.Opacity%2A> do retângulo para outro valor, seu código parece não ter efeito, porque a animação ainda está afetando a propriedade <xref:System.Windows.UIElement.Opacity%2A>.

Uma maneira de reobter o controle de uma propriedade animada no código é usar o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> e especificar NULL para o parâmetro <xref:System.Windows.Media.Animation.AnimationTimeline>. Para obter mais informações e um exemplo, consulte [definir uma propriedade depois de animá-la com um storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).

Observe que, embora a definição de um valor de propriedade que tenha uma animação <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> pareça não ter efeito, o valor da propriedade muda. Para obter mais informações, consulte a [visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md).

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>Associar dados e animar animações

A maioria das propriedades de animação pode ser vinculada a dados ou animada; por exemplo, você pode animar a propriedade <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de um <xref:System.Windows.Media.Animation.DoubleAnimation>. No entanto, devido ao modo como o sistema de temporização funciona, animações associadas a dados ou animadas não se comportam como outros objetos animados ou associados a dados. Para entender o seu comportamento, é importante entender o que significa aplicar uma animação a uma propriedade.

Consulte o exemplo na seção anterior que mostrou como animar o <xref:System.Windows.UIElement.Opacity%2A> de um retângulo. Quando o retângulo no exemplo anterior é carregado, seu gatilho de evento aplica o <xref:System.Windows.Media.Animation.Storyboard>. O sistema de temporização cria uma cópia do <xref:System.Windows.Media.Animation.Storyboard> e sua animação. Essas cópias são congeladas (feitas somente leitura) e os objetos <xref:System.Windows.Media.Animation.Clock> são criados a partir delas. Esses relógios fazem o verdadeiro trabalho de animar as propriedades usadas como destino.

O sistema de temporização cria um relógio para o <xref:System.Windows.Media.Animation.DoubleAnimation> e o aplica ao objeto e à propriedade especificados pelo <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> do <xref:System.Windows.Media.Animation.DoubleAnimation>. Nesse caso, o sistema de temporização aplica o relógio à propriedade <xref:System.Windows.UIElement.Opacity%2A> do objeto chamado "MyRectangle".

Embora um relógio também seja criado para a <xref:System.Windows.Media.Animation.Storyboard>, o relógio não é aplicado a nenhuma propriedade. Sua finalidade é controlar seu relógio filho, o relógio que é criado para o <xref:System.Windows.Media.Animation.DoubleAnimation>.

Para uma animação refletir as alterações de animação ou de associação de dados, seu relógio deve ser regenerado. Os relógios não são regenerados automaticamente para você. Para fazer uma animação refletir as alterações, reaplique seu storyboard usando um <xref:System.Windows.Media.Animation.BeginStoryboard> ou o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>. Quando você usa qualquer um desses métodos, a animação é reiniciada. No código, você pode usar o método <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> para deslocar o storyboard de volta para sua posição anterior.

Para obter um exemplo de uma animação associada a dados, consulte [exemplo de animação da chave spline](https://go.microsoft.com/fwlink/?LinkID=160011). Para obter mais informações sobre como funciona a animação e o sistema de temporização, consulte [visão geral do sistema de animação e tempo](animation-and-timing-system-overview.md).

<a name="otherWaysToAnimateSection"></a>

## <a name="other-ways-to-animate"></a>Outras maneiras de animar

Os exemplos nesta visão geral mostram como animar pelo uso de storyboards. Quando você usa código, você pode animar de várias outras maneiras. Para obter mais informações, consulte [visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md).

<a name="animation_samples"></a>

## <a name="animation-samples"></a>Amostras de animação

As amostras a seguir podem ajudá-lo a começar a adicionar animações a seus aplicativos.

- [Amostra de valores de destino de animação De, Para e Por](https://go.microsoft.com/fwlink/?LinkID=159988)

  Demonstra diferentes configurações De/Para/Por.

- [Amostra de comportamento de tempo da animação](https://go.microsoft.com/fwlink/?LinkID=159970)

  Demonstra as diferentes maneiras em que você pode controlar o comportamento de temporização de uma animação. Essa amostra também demonstra como associar o valor de destino de uma animação a dados.

<a name="related_topics"></a>

## <a name="related-topics"></a>Tópicos relacionados

|{1&gt;Título&lt;1}|Descrição|
|-----------|-----------------|
|[Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md)|Descreve como o sistema de tempo usa as classes <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock>, que permitem criar animações.|
|[Dicas e truques de animação](animation-tips-and-tricks.md)|Lista dicas úteis para solucionar problemas com animações, por exemplo, desempenho.|
|[Visão geral de animações personalizadas](custom-animations-overview.md)|Descreve como estender o sistema de animação com quadros chave, classes de animação ou retornos de chamada por quadro.|
|[Visão geral de animações de/para/por](from-to-by-animations-overview.md)|Descreve como criar uma animação que faz a transição entre dois valores.|
|[Visão geral das animações de quadro-chave](key-frame-animations-overview.md)|Descreve como criar uma animação com vários valores de destino, incluindo a capacidade de controlar o método de interpolação.|
|[Funções de easing](easing-functions.md)|Explica como aplicar fórmulas matemáticas às suas animações para obter comportamento realista, assim como saltar.|
|[Visão geral de animações de caminho](path-animations-overview.md)|Descreve como mover ou girar um objeto ao longo de um caminho complexo.|
|[Visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md)|Descreve as animações de propriedade usando storyboards, animações locais, relógios e animações por quadro.|
|[Visão geral de storyboards](storyboards-overview.md)|Descreve como usar storyboards com várias linhas do tempo para criar animações complexas.|
|[Visão geral dos comportamentos de tempo](timing-behaviors-overview.md)|Descreve os tipos de <xref:System.Windows.Media.Animation.Timeline> e as propriedades usadas em animações.|
|[Visão geral de eventos de tempo](timing-events-overview.md)|Descreve os eventos disponíveis nos objetos <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock> para executar o código em pontos na linha do tempo, como iniciar, pausar, retomar, ignorar ou parar.|
|[Tópicos de instruções](animation-and-timing-how-to-topics.md)|Contém exemplos de código para usar animações e linhas do tempo em seu aplicativo.|
|[Tópicos explicativos de relógios](clocks-how-to-topics.md)|Contém exemplos de código para usar o objeto <xref:System.Windows.Media.Animation.Clock> em seu aplicativo.|
|[Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)|Contém exemplos de código para usar animações de quadro chave em seu aplicativo.|
|[Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)|Contém exemplos de código para usar animações de caminho em seu aplicativo.|

<a name="reference"></a>

## <a name="reference"></a>Referência

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
