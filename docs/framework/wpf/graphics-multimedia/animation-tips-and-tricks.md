---
title: Dicas e truques de animação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
ms.openlocfilehash: ef59631663e6cf1c98adfed77a2dbdb6ca124fa1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636023"
---
# <a name="animation-tips-and-tricks"></a>Dicas e truques de animação
Ao trabalhar com animações no WPF, há várias dicas e truques que podem fazer com que suas animações tenham um desempenho melhor e poupar sua frustração.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Problemas gerais  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animar a posição de uma barra de rolagem ou controle deslizante os deixa congelados  
 Se você animar a posição de uma barra de rolagem ou controle deslizante usando uma animação que tenha uma <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (o valor padrão), o usuário não poderá mais mover a barra de rolagem ou o controle deslizante. Isso acontece porque, mesmo que a animação tenha terminado, ela ainda estará substituindo o valor base da propriedade de destino. Para impedir que a animação substitua o valor atual da propriedade, remova-o ou dê a ele um <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Para obter mais informações e um exemplo, consulte [definir uma propriedade depois de animá-la com um storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animar a saída de uma animação não tem nenhum efeito  
 Você não pode animar um objeto que é a saída de outra animação. Por exemplo, se você usar um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> para animar a <xref:System.Windows.Shapes.Shape.Fill%2A> de um <xref:System.Windows.Shapes.Rectangle> de um <xref:System.Windows.Media.RadialGradientBrush> para um <xref:System.Windows.Media.SolidColorBrush>, não será possível animar as propriedades do <xref:System.Windows.Media.RadialGradientBrush> ou <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Não é possível alterar o valor de uma propriedade após animá-la  
 Em alguns casos, pode parecer que não é possível alterar o valor de uma propriedade depois de ela ter sido animada, mesmo após o término da animação. Isso acontece porque, mesmo que a animação tenha terminado, ela ainda estará substituindo o valor base da propriedade. Para impedir que a animação substitua o valor atual da propriedade, remova-o ou dê a ele um <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Para obter mais informações e um exemplo, consulte [definir uma propriedade depois de animá-la com um storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Alterar uma linha do tempo não tem nenhum efeito  
 Embora a maioria das propriedades de <xref:System.Windows.Media.Animation.Timeline> seja animável e possa ser vinculada aos dados, alterar os valores de propriedade de um <xref:System.Windows.Media.Animation.Timeline> ativo parece não ter nenhum efeito. Isso ocorre porque, quando um <xref:System.Windows.Media.Animation.Timeline> é iniciado, o sistema de temporização faz uma cópia do <xref:System.Windows.Media.Animation.Timeline> e o utiliza para criar um objeto <xref:System.Windows.Media.Animation.Clock>. Modificar o original não causa nenhum efeito na cópia do sistema.  
  
 Para um <xref:System.Windows.Media.Animation.Timeline> refletir as alterações, seu relógio deve ser regenerado e usado para substituir o relógio criado anteriormente. Os relógios não são regenerados automaticamente para você. A seguir estão várias maneiras para aplicar alterações de linha do tempo:  
  
- Se a linha do tempo for ou pertencer a um <xref:System.Windows.Media.Animation.Storyboard>, você poderá fazê-lo refletir as alterações reaplicando seu storyboard usando um <xref:System.Windows.Media.Animation.BeginStoryboard> ou o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>. Isso tem o efeito colateral de também reiniciar a animação. No código, você pode usar o método <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> para avançar o storyboard de volta para sua posição anterior.  
  
- Se você aplicou uma animação diretamente a uma propriedade usando o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>, chame o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> novamente e passe-o para a animação que foi modificada.  
  
- Se você estiver trabalhando diretamente no nível do relógio, crie e aplique um novo conjunto de relógios e use-os para substituir o conjunto anterior de relógios gerados.  
  
 Para obter mais informações sobre cronogramas e relógios, consulte [visão geral do sistema de animação e tempo](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>O FillBehavior.Stop não funciona como o esperado  
 Há ocasiões em que a definição da propriedade <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> como <xref:System.Windows.Media.Animation.FillBehavior.Stop> parece não ter nenhum efeito, como quando uma animação "passa" para outra porque tem uma configuração <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> de <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 O exemplo a seguir cria uma <xref:System.Windows.Controls.Canvas>, uma <xref:System.Windows.Shapes.Rectangle> e uma <xref:System.Windows.Media.TranslateTransform>. O <xref:System.Windows.Media.TranslateTransform> será animado para mover o <xref:System.Windows.Shapes.Rectangle> em relação ao <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Os exemplos nesta seção usam os objetos anteriores para demonstrar vários casos em que a propriedade <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> não se comporta como você pode esperar.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" and HandoffBehavior com várias animações  
 Às vezes, parece que uma animação ignora sua propriedade <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> quando ela é substituída por uma segunda animação. Veja o exemplo a seguir, que cria dois objetos <xref:System.Windows.Media.Animation.Storyboard> e os usa para animar os mesmos <xref:System.Windows.Media.TranslateTransform> mostrados no exemplo anterior.  
  
 A primeira <xref:System.Windows.Media.Animation.Storyboard>, `B1`, anima a propriedade <xref:System.Windows.Media.TranslateTransform.X%2A> do <xref:System.Windows.Media.TranslateTransform> de 0 a 350, que move o retângulo 350 pixels para a direita. Quando a animação atinge o final de sua duração e para de reproduzir, a propriedade <xref:System.Windows.Media.TranslateTransform.X%2A> reverte para seu valor original, 0. Como resultado, o retângulo move-se para a direita em 350 pixels e, em seguida, retorna para a sua posição original.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 A segunda <xref:System.Windows.Media.Animation.Storyboard>, `B2`, também anima a propriedade <xref:System.Windows.Media.TranslateTransform.X%2A> da mesma <xref:System.Windows.Media.TranslateTransform>. Como apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> da animação neste <xref:System.Windows.Media.Animation.Storyboard> está definida, a animação usa o valor atual da propriedade que ele anima como seu valor inicial.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Se você clicar no segundo botão enquanto o primeiro <xref:System.Windows.Media.Animation.Storyboard> estiver em execução, poderá esperar o seguinte comportamento:  
  
1. O primeiro storyboard termina e envia o retângulo de volta para sua posição original, porque a animação tem uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2. O segundo storyboard entra em vigor e anima, da posição atual, que agora é 0, até a posição 500.  
  
 **Mas não isso o que acontece.** Em vez disso, o retângulo não retorna, mas continua se movendo para a direita. Isso acontece porque a segunda animação usa o valor atual da primeira animação como seu valor inicial e anima desse valor até o 500. Quando a segunda animação substitui a primeira porque o <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior> é usado, a <xref:System.Windows.Media.Animation.FillBehavior> da primeira animação não importa.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior e o evento concluído  
 Os exemplos a seguir demonstram outro cenário no qual o <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> parece não ter nenhum efeito. Novamente, o exemplo usa um Storyboard para animar a propriedade <xref:System.Windows.Media.TranslateTransform.X%2A> do <xref:System.Windows.Media.TranslateTransform> de 0 a 350. No entanto, desta vez o exemplo registra para o evento <xref:System.Windows.Media.Animation.Timeline.Completed>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 O manipulador de eventos <xref:System.Windows.Media.Animation.Timeline.Completed> inicia outra <xref:System.Windows.Media.Animation.Storyboard> que anima a mesma propriedade de seu valor atual para 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 A seguir está a marcação que define a segunda <xref:System.Windows.Media.Animation.Storyboard> como um recurso.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Ao executar o <xref:System.Windows.Media.Animation.Storyboard>, você pode esperar que a propriedade <xref:System.Windows.Media.TranslateTransform.X%2A> da <xref:System.Windows.Media.TranslateTransform> anime de 0 a 350 e, em seguida, reverter para 0 após a conclusão (porque ela tem uma configuração de <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>) e, em seguida, animar de 0 a 500. Em vez disso, o <xref:System.Windows.Media.TranslateTransform> anima de 0 a 350 e, em seguida, para 500.  
  
 Isso ocorre por causa da ordem em que o WPF gera eventos e porque os valores de propriedade são armazenados em cache e não são recalculados, a menos que a propriedade seja invalidada. O evento <xref:System.Windows.Media.Animation.Timeline.Completed> é processado primeiro porque foi disparado pela linha do tempo raiz (a primeira <xref:System.Windows.Media.Animation.Storyboard>). Neste momento, a propriedade <xref:System.Windows.Media.TranslateTransform.X%2A> ainda retorna seu valor animado porque ainda não foi invalidada. A segunda <xref:System.Windows.Media.Animation.Storyboard> usa o valor armazenado em cache como seu valor inicial e começa a animação.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Desempenho  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>As animações continuam a ser executadas depois de sair de uma página  
 Quando você sai de um <xref:System.Windows.Controls.Page> que contém animações em execução, essas animações continuarão a ser executadas até que o <xref:System.Windows.Controls.Page> seja coletado pelo lixo. Dependendo do sistema de navegação que você está usando, uma página da qual você sai talvez continue na memória por um tempo indefinido, consumindo recursos com as animações. Isso é mais perceptível quando uma página contém animações em constante execução ("ambiente").  
  
 Por esse motivo, é uma boa ideia usar o evento <xref:System.Windows.FrameworkElement.Unloaded> para remover animações quando você navega para fora de uma página.  
  
 Há diferentes maneiras de remover uma animação. As técnicas a seguir podem ser usadas para remover as animações que pertencem a um <xref:System.Windows.Media.Animation.Storyboard>.  
  
- Para remover um <xref:System.Windows.Media.Animation.Storyboard> iniciado com um gatilho de evento, consulte [como remover um storyboard](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Para usar o código para remover um <xref:System.Windows.Media.Animation.Storyboard>, consulte o método <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>.  
  
 A próxima técnica pode ser usada independentemente de como a animação foi iniciada.  
  
- Para remover animações de uma propriedade específica, use o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>. Especifique a propriedade que está sendo animada como o primeiro parâmetro e `null` como a segunda. Isso removerá todos os relógios de animação da propriedade.  
  
 Para obter mais informações sobre as diferentes maneiras de animar propriedades, consulte [visão geral das técnicas de animação de propriedades](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>O uso do HandoffBehavior composto consome recursos do sistema  
 Quando você aplica uma <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>ou <xref:System.Windows.Media.Animation.AnimationClock> a uma propriedade usando o <xref:System.Windows.Media.Animation.HandoffBehavior>de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, os objetos <xref:System.Windows.Media.Animation.Clock> associados anteriormente a essa propriedade continuam a consumir recursos do sistema; o sistema de tempo não removerá esses relógios automaticamente.  
  
 Para evitar problemas de desempenho ao aplicar um grande número de relógios usando <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, você deve remover os relógios de composição da propriedade animada depois que eles forem concluídos. Há várias maneiras para remover um relógio.  
  
- Para remover todos os relógios de uma propriedade, use o <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> ou o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> do objeto animado. Especifique a propriedade que está sendo animada como o primeiro parâmetro e `null` como a segunda. Isso removerá todos os relógios de animação da propriedade.  
  
- Para remover um <xref:System.Windows.Media.Animation.AnimationClock> específico de uma lista de relógios, use a propriedade <xref:System.Windows.Media.Animation.Clock.Controller%2A> da <xref:System.Windows.Media.Animation.AnimationClock> para recuperar um <xref:System.Windows.Media.Animation.ClockController>e, em seguida, chame o método <xref:System.Windows.Media.Animation.ClockController.Remove%2A> do <xref:System.Windows.Media.Animation.ClockController>. Normalmente, isso é feito no manipulador de eventos <xref:System.Windows.Media.Animation.Clock.Completed> para um relógio. Observe que somente os relógios raiz podem ser controlados por um <xref:System.Windows.Media.Animation.ClockController>; a propriedade <xref:System.Windows.Media.Animation.Clock.Controller%2A> de um relógio filho retornará `null`. Observe também que o evento <xref:System.Windows.Media.Animation.Clock.Completed> não será chamado se a duração efetiva do relógio for indefinidamente.  Nesse caso, o usuário precisará determinar quando chamar <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Isso é basicamente um problema para animações em objetos que têm um longo tempo de vida.  Quando um objeto passa pela coleta de lixo, seus relógios também serão desconectados e coletados como lixo.  
  
 Para obter mais informações sobre objetos de relógio, consulte [visão geral do sistema de animação e tempo](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Veja também

- [Visão geral da animação](animation-overview.md)
