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
ms.openlocfilehash: 5fb9550ddce4ead900206c2ece2f976ab8b42c4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558324"
---
# <a name="animation-overview"></a>Visão geral da animação
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Fornece um conjunto avançado de recursos gráficos e de layout que permitem a criação de interfaces de usuário atrativas e documentos atraentes. A animação pode tornar uma interface do usuário ainda mais espetacular e utilizável. Apenas uma cor de fundo animada ou aplicando um animado <xref:System.Windows.Media.Transform>, você pode criar transições dramáticas de tela ou fornecem indicações visuais úteis.  
  
 Esta visão geral fornece uma introdução para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animação e sistema de tempo. Ele se concentra na animação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos usando storyboards.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Introdução a animações  
 A animação é uma ilusão criada passando-se rapidamente por uma série de imagens, cada uma ligeiramente diferente da anterior. O cérebro vê a sequência de imagens como uma única cena em mudança. Em filmes, essa ilusão é criada usando câmeras que gravam várias fotografias, ou quadros, a cada segundo. Quando os quadros são executados por um projetor, o público-alvo vê um filme animado.  
  
 A animação em um computador é semelhante. Por exemplo, um programa que cria um desenho de um retângulo que desaparece pode funcionar conforme descrito a seguir.  
  
-   O programa cria um temporizador.  
  
-   O programa verifica o temporizador em intervalos definidos para ver quanto tempo transcorreu.  
  
-   Cada vez que o programa verifica o temporizador, ele calcula o valor de opacidade atual para o retângulo com base em quanto tempo transcorreu.  
  
-   O programa então atualiza o retângulo com o novo valor e o redesenha.  
  
 Antes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] os desenvolvedores precisavam criar e gerenciar seus próprios sistemas de controle de tempo ou usar bibliotecas personalizadas especiais. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui um sistema eficiente de tempo que é exposto por meio de código gerenciado e [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e que está profundamente integrado ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework. A animação do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] facilita a animação de controles e outros objetos gráficos.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realiza todo o trabalho nos bastidores para gerenciar um sistema de temporização e redesenhar a tela de modo eficiente. Ele fornece classes de temporização que permitem que você se concentre nos efeitos que deseja criar, em vez de precisar concentrar-se na mecânica envolvida para atingir tais efeitos. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também torna fácil criar sua própria animação expondo classes de animação base das quais suas classes podem herdar, para assim produzir animações personalizadas. Essas animações personalizadas obtêm muitos dos benefícios de desempenho das classes de animação padrão.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>Sistema de Animação de Propriedades do WPF  
 Se você entender alguns conceitos importantes sobre o sistema de temporização [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animações podem ser mais fácil de usar. Mais importante é que, em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animar objetos ao aplicar animações a suas propriedades individuais. Por exemplo, para um elemento de framework crescer, você anima seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades. Para fazer com que um objeto desaparecer da exibição, você animar seu <xref:System.Windows.UIElement.Opacity%2A> propriedade.  
  
 Para uma propriedade ter capacidade de animação, ela deve atender aos três requisitos a seguir:  
  
-   Ela deve ser uma propriedade de dependência.  
  
-   Ela deve pertencer a uma classe que herda de <xref:System.Windows.DependencyObject> e implementa o <xref:System.Windows.Media.Animation.IAnimatable> interface.  
  
-   Deve haver um tipo de animação compatível disponível. (Se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não fornecer um, você pode criar seus próprios. Consulte o [visão geral de animações personalizadas](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contém muitos objetos que têm <xref:System.Windows.Media.Animation.IAnimatable> propriedades. Controla como <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.TabControl>e também <xref:System.Windows.Controls.Panel> e <xref:System.Windows.Shapes.Shape> objetos herdam <xref:System.Windows.DependencyObject>. A maioria de suas propriedades são propriedades de dependência.  
  
 Você pode usar animações em quase qualquer lugar, o que inclui em estilos e modelos de controle. Animações não precisam ser visuais; você pode animar objetos que não fazem parte da interface do usuário se eles atendem aos critérios descritos nesta seção.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Exemplo: fazer com que um elemento apareça e desapareça da exibição  
 Este exemplo mostra como usar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animação para animar o valor de uma propriedade de dependência. Ele usa um <xref:System.Windows.Media.Animation.DoubleAnimation>, que é um tipo de animação que gera <xref:System.Double> valores, para animar a <xref:System.Windows.UIElement.Opacity%2A> propriedade de um <xref:System.Windows.Shapes.Rectangle>. Como resultado, o <xref:System.Windows.Shapes.Rectangle> desaparece e sair do modo de exibição.  
  
 A primeira parte do exemplo cria um <xref:System.Windows.Shapes.Rectangle> elemento. As etapas a seguir mostram como criar uma animação e aplicá-lo para o retângulo <xref:System.Windows.UIElement.Opacity%2A> propriedade.
  
 A seguir mostra como criar um <xref:System.Windows.Shapes.Rectangle> elemento em um <xref:System.Windows.Controls.StackPanel> em XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 A seguir mostra como criar um <xref:System.Windows.Shapes.Rectangle> elemento em um <xref:System.Windows.Controls.StackPanel> no código.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>Parte 1: criar uma DoubleAnimation  
 É uma maneira de tornar um elemento desaparecer e sair do modo de exibição animar seu <xref:System.Windows.UIElement.Opacity%2A> propriedade. Porque o <xref:System.Windows.UIElement.Opacity%2A> é de propriedade do tipo <xref:System.Double>, você precisa de uma animação que produz valores double. A <xref:System.Windows.Media.Animation.DoubleAnimation> é uma destas animação. Um <xref:System.Windows.Media.Animation.DoubleAnimation> cria uma transição entre dois valores double. Para especificar seu valor inicial, defina seu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade. Para especificar o valor final, defina seu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.  
  
1.  Um valor de opacidade `1.0` faz com que o objeto completamente opaco e um valor de opacidade `0.0` torna completamente invisível. Para fazer a transição de animação de `1.0` para `0.0` você definir seu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade `1.0` e sua <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade `0.0`. A seguir mostra como criar um <xref:System.Windows.Media.Animation.DoubleAnimation> em XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     A seguir mostra como criar um <xref:System.Windows.Media.Animation.DoubleAnimation> no código.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  Em seguida, você deve especificar um <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. O <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma animação especifica quanto tempo demora para ir do seu valor inicial para o valor de destino. A seguir mostra como definir o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> como cinco segundos em XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     A seguir mostra como definir o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a cinco segundos no código.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  O código anterior mostrou uma animação que faz a transição de `1.0` para `0.0`, que faz com que o elemento de destino vá de completamente opaco para completamente invisível. Para fazer o elemento no modo de exibição depois de sumir, defina o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade da animação para `true`. Para repetir a animação indefinidamente, defina seu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. A seguir mostra como definir o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> e <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedades em XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     A seguir mostra como definir o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> e <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedades no código.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>Parte 2: criar um storyboard  
 Para aplicar uma animação a um objeto, você cria um <xref:System.Windows.Media.Animation.Storyboard> e usar o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> nas propriedades para especificar o objeto e propriedade para animar.  
  
1.  Criar o <xref:System.Windows.Media.Animation.Storyboard> e adicione a animação como seu filho. A seguir mostra como criar o <xref:System.Windows.Media.Animation.Storyboard> em XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     Para criar o <xref:System.Windows.Media.Animation.Storyboard> no código, declare um <xref:System.Windows.Media.Animation.Storyboard> variável no nível de classe.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Em seguida, inicializar o <xref:System.Windows.Media.Animation.Storyboard> e adicione a animação como seu filho.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  O <xref:System.Windows.Media.Animation.Storyboard> deve saber onde aplicar a animação. Use o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> propriedade para especificar o objeto para animar anexada. A seguir mostra como definir o nome de destino do <xref:System.Windows.Media.Animation.DoubleAnimation> para `MyRectangle` em XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     A seguir mostra como definir o nome de destino do <xref:System.Windows.Media.Animation.DoubleAnimation> para `MyRectangle` no código.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  Use o <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> propriedade para especificar a propriedade para animar anexada. A seguir mostra como a animação é configurada para o destino a <xref:System.Windows.UIElement.Opacity%2A> propriedade o <xref:System.Windows.Shapes.Rectangle> em XAML.
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     A seguir mostra como a animação é configurada para o destino de <xref:System.Windows.UIElement.Opacity%2A> propriedade do <xref:System.Windows.Shapes.Rectangle> no código.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Para obter mais informações sobre <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> sintaxe e exemplos adicionais, consulte o [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Parte 3 (XAML): associar o storyboard com um gatilho  
 A maneira mais fácil de aplicar e começar um <xref:System.Windows.Media.Animation.Storyboard> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é usar um gatilho de evento. Esta seção mostra como associar o <xref:System.Windows.Media.Animation.Storyboard> com um gatilho em XAML.  
  
1.  Criar um <xref:System.Windows.Media.Animation.BeginStoryboard> do objeto e associar seu storyboard a ele. Um <xref:System.Windows.Media.Animation.BeginStoryboard> é um tipo de <xref:System.Windows.TriggerAction> que se aplica e inicia um <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  Criar um <xref:System.Windows.EventTrigger> e adicione o <xref:System.Windows.Media.Animation.BeginStoryboard> para sua <xref:System.Windows.EventTrigger.Actions%2A> coleção. Definir o <xref:System.Windows.EventTrigger.RoutedEvent%2A> propriedade do <xref:System.Windows.EventTrigger> do evento roteado que você deseja iniciar o <xref:System.Windows.Media.Animation.Storyboard>. (Para obter mais informações sobre eventos roteados, consulte o [visão geral sobre eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md).)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  Adicionar o <xref:System.Windows.EventTrigger> para o <xref:System.Windows.FrameworkElement.Triggers%2A> coleção do retângulo.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Parte 3 (código): associar o storyboard com um manipulador de eventos  
 A maneira mais fácil de aplicar e começar um <xref:System.Windows.Media.Animation.Storyboard> no código é usar um manipulador de eventos. Esta seção mostra como associar o <xref:System.Windows.Media.Animation.Storyboard> com um manipulador de eventos no código.  
  
1.  Registre-se para o <xref:System.Windows.FrameworkElement.Loaded> eventos do retângulo.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  Declare o manipulador de eventos. No manipulador de eventos, use o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método para aplicar o storyboard.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Exemplo completo  
 O exemplo a seguir mostra como criar um retângulo que desaparece e sair do modo de exibição em XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 O exemplo a seguir mostra como criar um retângulo que aparece e desaparece de exibição no código.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Tipos de animação  
 Já que as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade que utiliza um <xref:System.Double>, como o <xref:System.Windows.FrameworkElement.Width%2A> propriedade de um elemento, use uma animação que produz <xref:System.Double> valores. Para animar uma propriedade que utiliza um <xref:System.Windows.Point>, use uma animação que produz <xref:System.Windows.Point> valores e assim por diante. Devido ao número de tipos de propriedades diferentes, existem várias classes de animação no <xref:System.Windows.Media.Animation> namespace. Felizmente, elas seguem uma convenção de nomenclatura estrita que facilita a diferenciação entre elas:  
  
-   \<*Tipo*> animação  
  
     Conhecida como "de/para/por" ou animação "básica", ela anima entre um valor inicial e outro de destino, ou então pela adição de um valor de deslocamento ao seu valor inicial.  
  
    -   Para especificar um valor inicial, defina a propriedade De da animação.  
  
    -   Para especificar um valor final, defina a propriedade Para da animação.  
  
    -   Para especificar um valor de deslocamento, defina a propriedade Por da animação.  
  
     Os exemplos nesta visão geral usam essas animações porque elas são mais simples de usar. Animações de/para/por são descritas detalhadamente na visão geral From/To/By animações.  
  
-   \<*Tipo*> AnimationUsingKeyFrames  
  
     Animações de quadro chave são mais avançadas que animações de/para/por porque você pode especificar qualquer número de valores de destino e até mesmo controlar seu método de interpolação. Alguns tipos só podem ser animados com animações de quadro chave. Animações de quadro-chave são descritas detalhadamente o [visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   \<*Tipo*> AnimationUsingPath  
  
     Animações de caminho permitem que você use um caminho geométrico para produzir valores animados.  
  
-   \<*Tipo*> AnimationBase  
  
     Classe abstrata que, quando você implementa, anima um \< *tipo*> valor. Esta classe serve como a classe base para \< *tipo*> animação e \< *tipo*> AnimationUsingKeyFrames de classes. Você só precisará lidar diretamente com essas classes se quiser criar suas próprias animações personalizadas. Caso contrário, use um \< *tipo*> Animation ou KeyFrame\<*tipo*> animação.  
  
 Na maioria dos casos, você desejará usar o \< *tipo*> classes de animação, como <xref:System.Windows.Media.Animation.DoubleAnimation> e <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 A tabela a seguir mostra vários tipos de animação comuns e algumas propriedades com as qual eles são usados.  
  
|Tipo de propriedade|Animação básica (De/Para/Por) correspondente|Animação de quadro chave correspondente|Animação de caminho correspondente|Exemplo de uso|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Nenhum|Animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> ou <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animar a <xref:System.Windows.FrameworkElement.Width%2A> de um <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.FrameworkElement.Height%2A> de um <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animar a <xref:System.Windows.Media.EllipseGeometry.Center%2A> posição de um <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Nenhum|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Nenhum|Animar a <xref:System.Windows.Controls.TextBlock.Text%2A> de um <xref:System.Windows.Controls.TextBlock> ou <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>As animações são linhas do tempo  
 Todos os tipos de animação herdam o <xref:System.Windows.Media.Animation.Timeline> classe; portanto, todas as animações são tipos especializados de linhas de tempo. Um <xref:System.Windows.Media.Animation.Timeline> define um segmento de tempo. Você pode especificar o *comportamentos de temporização* de uma linha do tempo: seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, quantas vezes é repetido e até mesmo tempo como rápido para ele.  
  
 Como uma animação é um <xref:System.Windows.Media.Animation.Timeline>, ela também representa um segmento de tempo. Uma animação também calcula valores de saída enquanto processa através do segmento de tempo especificado (ou <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Conforme a animação progride ou é "reproduzida", ela atualiza a propriedade com a qual está associada.  
  
 Três propriedades de temporização frequentemente usadas são <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, e <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>A propriedade Duration  
 Conforme mencionado anteriormente, uma linha do tempo representa um segmento de tempo. O comprimento do segmento é determinado pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A> da linha do tempo, geralmente é especificada usando um <xref:System.Windows.Duration.TimeSpan%2A> valor. Quando uma linha do tempo atinge o final de sua duração, ela completou uma iteração.  
  
 Uma animação usa sua <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade para determinar seu valor atual. Se você não especificar um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> valor uma animação, ela usa 1 segundo, que é o padrão.  
  
 A sintaxe a seguir mostra uma versão simplificada do [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atributo sintaxe para a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade.  
  
*horas* `:` *minutos* `:` *segundos*
  
 A tabela a seguir mostra vários <xref:System.Windows.Duration> configurações e seus valores resultantes.  
  
|Configuração|Valor resultante|  
|-------------|---------------------|  
|0:0:5.5|5,5 segundos.|  
|0:30:5.5|30 minutos e 5,5 segundos.|  
|1:30:5.5|1 hora, 30 minutos e 5,5 segundos.|  
  
 Uma maneira de especificar um <xref:System.Windows.Duration> no código é usar o <xref:System.TimeSpan.FromSeconds%2A> método para criar um <xref:System.TimeSpan>, em seguida, declarar uma nova <xref:System.Windows.Duration> estrutura usando essa <xref:System.TimeSpan>.  
  
 Para obter mais informações sobre <xref:System.Windows.Duration> valores e completo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sintaxe, consulte o <xref:System.Windows.Duration> estrutura.  
  
#### <a name="autoreverse"></a>AutoReverse  
 O <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade especifica se uma linha de tempo reproduz de volta após atingir o final de seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Se você definir esta propriedade de animação `true`, uma animação volta depois que ele atinge o final de seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, tocando do valor final para o seu valor inicial. Por padrão, essa propriedade é `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 O <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade especifica quantas vezes uma linha de tempo é reproduzida. Por padrão, linhas de tempo tem uma contagem de iteração de `1.0`, que significa que elas tocam uma vez e não repita.  
  
 Para obter mais informações sobre essas propriedades e outras, consulte o [visão geral de comportamentos de tempo](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Aplicar uma animação a uma propriedade  
 As seções anteriores descrevem os diferentes tipos de animações e suas propriedades de temporização. Esta seção mostra como aplicar a animação à propriedade que você deseja animar. <xref:System.Windows.Media.Animation.Storyboard> objetos fornecem uma maneira de aplicar animações a propriedades. Um <xref:System.Windows.Media.Animation.Storyboard> é um *cronograma contêiner* que fornece informações de direcionamento para as animações que ele contém.  
  
### <a name="targeting-objects-and-properties"></a>Usar objetos e propriedades como destino  
 O <xref:System.Windows.Media.Animation.Storyboard> classe fornece a <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> propriedades anexadas. Ao definir essas propriedades em uma animação, você diz à animação o que animar. No entanto, antes de uma animação poder usar um objeto como destino, normalmente esse objeto deverá receber um nome.  
  
 Atribuir um nome para um <xref:System.Windows.FrameworkElement> é diferente de atribuir um nome para um <xref:System.Windows.Freezable> objeto. A maioria dos controles e painéis são elementos framework; no entanto, a maioria dos objetos puramente gráficos como pincéis, transformações e geometrias são objetos congeláveis. Se você não tiver certeza se um tipo é um <xref:System.Windows.FrameworkElement> ou um <xref:System.Windows.Freezable>, consulte o **hierarquia de herança** seção de sua documentação de referência.  
  
-   Para fazer um <xref:System.Windows.FrameworkElement> um destino de animação, você dê a ele um nome, definindo seu <xref:System.Windows.FrameworkElement.Name%2A> propriedade. No código, você também deve usar o <xref:System.Windows.FrameworkElement.RegisterName%2A> método para registrar o nome do elemento na página ao qual ele pertence.  
  
-   Para fazer um <xref:System.Windows.Freezable> objeto um destino de animação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você usa o [diretiva X:Name](../../../../docs/framework/xaml-services/x-name-directive.md) para atribuir um nome. No código, que você acabou de usar o <xref:System.Windows.FrameworkElement.RegisterName%2A> método para registrar o objeto com a página ao qual ele pertence.  
  
 As seções a seguir fornecem um exemplo de nomeação de um elemento em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e código. Para obter informações mais detalhadas sobre nomeação e alvo, consulte o [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Aplicar e iniciar Storyboards  
 Para iniciar um storyboard no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], associe-o com um <xref:System.Windows.EventTrigger>. Um <xref:System.Windows.EventTrigger> é um objeto que descreve quais ações a serem tomadas quando ocorre um evento especificado. Uma dessas ações pode ser um <xref:System.Windows.Media.Animation.BeginStoryboard> ação, que você usa para iniciar seu storyboard. Gatilhos de evento são semelhantes ao conceito de manipuladores de eventos porque eles permitem que você especifique como o aplicativo responde a um evento específico. Diferentemente de manipuladores de eventos, os disparadores de evento podem ser totalmente descritos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; nenhum outro código é necessário.  
  
 Para iniciar um <xref:System.Windows.Media.Animation.Storyboard> no código, você pode usar um <xref:System.Windows.EventTrigger> ou use o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método o <xref:System.Windows.Media.Animation.Storyboard> classe.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Controlar interativamente um storyboard  
 O exemplo anterior mostrou como iniciar um <xref:System.Windows.Media.Animation.Storyboard> quando ocorre um evento. Você também pode interativamente controlar um <xref:System.Windows.Media.Animation.Storyboard> depois de iniciar: você pode pausar, retomar, interromper, Avançar para completar seu período, buscar e remover o <xref:System.Windows.Media.Animation.Storyboard>. Para obter mais informações e um exemplo que mostra como controlar interativamente um <xref:System.Windows.Media.Animation.Storyboard>, consulte o [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>O que acontece após o término da animação?  
 O <xref:System.Windows.Media.Animation.FillBehavior> propriedade especifica como uma linha do tempo se comporta quando ela termina. Por padrão, uma linha de tempo inicia <xref:System.Windows.Media.Animation.ClockState.Filling> quando ele termina. Uma animação que é <xref:System.Windows.Media.Animation.ClockState.Filling> mantém o valor de saída final.  
  
 O <xref:System.Windows.Media.Animation.DoubleAnimation> no exemplo anterior não acaba porque sua <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> está definida como <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. O exemplo a seguir anima um retângulo usando uma animação similar. Ao contrário do exemplo anterior, o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> e <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> dessa animação são deixadas em seus valores padrão. Portanto, a animação avança de 1 para 0 durante cinco segundos e, em seguida, é interrompida.  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Porque seu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> não foi alterado do valor padrão, que é <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, a animação mantém seu valor final, 0, quando ele termina. Portanto, o <xref:System.Windows.UIElement.Opacity%2A> do retângulo é mantido em 0 depois que a animação termina. Se você definir o <xref:System.Windows.UIElement.Opacity%2A> do retângulo para outro valor, seu código parece não ter nenhum efeito, porque a animação ainda está afetando o <xref:System.Windows.UIElement.Opacity%2A> propriedade.  
  
 Uma maneira de recuperar o controle de uma propriedade animada em código é usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método e especifique null para o <xref:System.Windows.Media.Animation.AnimationTimeline> parâmetro. Para obter mais informações e um exemplo, consulte [definir uma propriedade após animação-o com um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Observe que, embora definir um valor de propriedade que tem um <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> animação parece não ter nenhum efeito, altere o valor da propriedade. Para obter mais informações, consulte o [visão geral do sistema de controle de tempo e animação](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Associar dados e animar animações  
 A maioria das propriedades de animação podem ser associadas a dados ou animadas; Por exemplo, é possível animar a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade de um <xref:System.Windows.Media.Animation.DoubleAnimation>. No entanto, devido ao modo como o sistema de temporização funciona, animações associadas a dados ou animadas não se comportam como outros objetos animados ou associados a dados. Para entender o seu comportamento, é importante entender o que significa aplicar uma animação a uma propriedade.  
  
 Consulte o exemplo na seção anterior que mostrou como animar o <xref:System.Windows.UIElement.Opacity%2A> de um retângulo. Quando o retângulo no exemplo anterior é carregado, seu gatilho de evento se aplica a <xref:System.Windows.Media.Animation.Storyboard>. O sistema de temporização cria uma cópia do <xref:System.Windows.Media.Animation.Storyboard> e sua animação. Essas cópias são congeladas (somente leitura) e <xref:System.Windows.Media.Animation.Clock> objetos são criados a partir delas. Esses relógios fazem o verdadeiro trabalho de animar as propriedades usadas como destino.  
  
 O sistema de temporização cria um relógio para o <xref:System.Windows.Media.Animation.DoubleAnimation> e aplica-se ao objeto e propriedade que é especificada pelo <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation>. Nesse caso, o sistema de temporização aplica o relógio para o <xref:System.Windows.UIElement.Opacity%2A> propriedade do objeto de nome "MyRetangle".  
  
 Embora um relógio também seja criado para o <xref:System.Windows.Media.Animation.Storyboard>, o relógio não é aplicado a todas as propriedades. Sua finalidade é controlar seus relógios filhos, o relógio que é criado para o <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Para uma animação refletir as alterações de animação ou de associação de dados, seu relógio deve ser regenerado. Os relógios não são regenerados automaticamente para você. Para fazer uma animação refletir mudanças, reaplique seu storyboard usando um <xref:System.Windows.Media.Animation.BeginStoryboard> ou <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método. Quando você usa qualquer um desses métodos, a animação é reiniciada. No código, você pode usar o <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método para reposicionar o storyboard de volta para sua posição anterior.  
  
 Para um exemplo de dados de animação associada, consulte [chave Spline Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160011). Para obter mais informações sobre como funciona o sistema de animação e de tempo, consulte [visão geral do sistema de controle de tempo e animação](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Outras maneiras de animar  
 Os exemplos nesta visão geral mostram como animar pelo uso de storyboards. Quando você usa código, você pode animar de várias outras maneiras. Para obter mais informações, consulte o [visão geral de técnicas de animação de propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Amostras de animação  
 As amostras a seguir podem ajudá-lo a começar a adicionar animações a seus aplicativos.  
  
-   [Amostra de valores de destino de animação De, Para e Por](http://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Demonstra diferentes configurações De/Para/Por.  
  
-   [Amostra de comportamento de tempo da animação](http://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Demonstra as diferentes maneiras em que você pode controlar o comportamento de temporização de uma animação. Essa amostra também demonstra como associar o valor de destino de uma animação a dados.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Visão geral da animação e do sistema de tempo](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|Descreve como o sistema de tempo usa o <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock> classes, que permitem que você crie animações.|  
|[Dicas e truques de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|Lista dicas úteis para solucionar problemas com animações, por exemplo, desempenho.|  
|[Visão geral de animações personalizadas](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|Descreve como estender o sistema de animação com quadros chave, classes de animação ou retornos de chamada por quadro.|  
|Visão geral de animações de/para/por|Descreve como criar uma animação que faz a transição entre dois valores.|  
|[Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|Descreve como criar uma animação com vários valores de destino, incluindo a capacidade de controlar o método de interpolação.|  
|[Funções de easing](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|Explica como aplicar fórmulas matemáticas às suas animações para obter comportamento realista, assim como saltar.|  
|[Visão geral de animações de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|Descreve como mover ou girar um objeto ao longo de um caminho complexo.|  
|[Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|Descreve as animações de propriedade usando storyboards, animações locais, relógios e animações por quadro.|  
|[Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|Descreve como usar storyboards com várias linhas do tempo para criar animações complexas.|  
|[Visão geral dos comportamentos de tempo](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|Descreve o <xref:System.Windows.Media.Animation.Timeline> tipos e propriedades usadas em animações.|  
|[Visão geral de eventos de tempo](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|Descreve os eventos disponíveis sobre o <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock> objetos para executar o código em pontos na linha do tempo, como iniciar, pausar, retomar, ignorar ou parar.|  
|[Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|Contém exemplos de código para usar animações e linhas do tempo em seu aplicativo.|  
|[Tópicos explicativos de relógios](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|Contém exemplos de código para usar o <xref:System.Windows.Media.Animation.Clock> objeto em seu aplicativo.|  
|[Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|Contém exemplos de código para usar animações de quadro chave em seu aplicativo.|  
|[Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|Contém exemplos de código para usar animações de caminho em seu aplicativo.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Referência  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
