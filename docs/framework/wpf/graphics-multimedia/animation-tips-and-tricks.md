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
ms.openlocfilehash: 2fcabf178eb9d1b56582422204c6a745c6388a85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="animation-tips-and-tricks"></a>Dicas e truques de animação
Ao trabalhar com animações na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], há um número de dicas e truques que podem tornar as animações têm melhor desempenho e poupar frustração.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Problemas gerais  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animar a posição de uma barra de rolagem ou controle deslizante os deixa congelados  
 Se você animar a posição de uma barra de rolagem ou controle deslizante usando uma animação que tem um <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (o valor padrão), o usuário não será capaz de mover o controle deslizante ou a barra de rolagem. Isso acontece porque, mesmo que a animação tenha terminado, ela ainda estará substituindo o valor base da propriedade de destino. Para interromper a animação substitua o valor da propriedade atual, remova-o ou dê a ele um <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Para obter mais informações e um exemplo, consulte [definir uma propriedade após animação-o com um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animar a saída de uma animação não tem nenhum efeito  
 Você não pode animar um objeto que é a saída de outra animação. Por exemplo, se você usar um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> para animar a <xref:System.Windows.Shapes.Shape.Fill%2A> de um <xref:System.Windows.Shapes.Rectangle> de um <xref:System.Windows.Media.RadialGradientBrush> para um <xref:System.Windows.Media.SolidColorBrush>, não é possível animar quaisquer propriedades do <xref:System.Windows.Media.RadialGradientBrush> ou <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Não é possível alterar o valor de uma propriedade após animá-la  
 Em alguns casos, pode parecer que não é possível alterar o valor de uma propriedade depois de ela ter sido animada, mesmo após o término da animação. Isso acontece porque, mesmo que a animação tenha terminado, ela ainda estará substituindo o valor base da propriedade. Para interromper a animação substitua o valor da propriedade atual, remova-o ou dê a ele um <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Para obter mais informações e um exemplo, consulte [definir uma propriedade após animação-o com um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Alterar uma linha do tempo não tem nenhum efeito  
 Embora a maioria dos <xref:System.Windows.Media.Animation.Timeline> propriedades são pode ser animadas e podem ser associada a dados, alterar os valores de propriedade de um ativo <xref:System.Windows.Media.Animation.Timeline> parece não ter nenhum efeito. Isso ocorre porque, quando um <xref:System.Windows.Media.Animation.Timeline> é iniciada, o sistema de tempo faz uma cópia do <xref:System.Windows.Media.Animation.Timeline> e usa-o para criar um <xref:System.Windows.Media.Animation.Clock> objeto. Modificar o original não causa nenhum efeito na cópia do sistema.  
  
 Para um <xref:System.Windows.Media.Animation.Timeline> para refletir as alterações, seu relógio deve ser regenerado e usado para substituir o relógio criado anteriormente. Os relógios não são regenerados automaticamente para você. A seguir estão várias maneiras para aplicar alterações de linha do tempo:  
  
-   Se o cronograma for ou pertence a um <xref:System.Windows.Media.Animation.Storyboard>, você pode torná-lo refletir alterações reaplicando seu storyboard usando um <xref:System.Windows.Media.Animation.BeginStoryboard> ou <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método. Isso tem o efeito colateral de também reiniciar a animação. No código, você pode usar o <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método para avançar o storyboard de volta para sua posição anterior.  
  
-   Se você aplicar uma animação diretamente a uma propriedade usando o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método, chame o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método novamente e passá-lo a animação que foi modificada.  
  
-   Se você estiver trabalhando diretamente no nível do relógio, crie e aplique um novo conjunto de relógios e use-os para substituir o conjunto anterior de relógios gerados.  
  
 Para obter mais informações sobre cronogramas e relógios, consulte [visão geral do sistema de controle de tempo e animação](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>O FillBehavior.Stop não funciona como o esperado  
 Há ocasiões ao definir o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade <xref:System.Windows.Media.Animation.FillBehavior.Stop> parece não ter nenhum efeito, como quando uma animação "transmite" para outra porque ele tem um <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> configuração de <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Canvas>, um <xref:System.Windows.Shapes.Rectangle> e um <xref:System.Windows.Media.TranslateTransform>. O <xref:System.Windows.Media.TranslateTransform> será animado para mover o <xref:System.Windows.Shapes.Rectangle> em torno de <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Os exemplos nesta seção usam os objetos anteriores para demonstrar vários casos onde o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade não se comportar conforme o esperado para.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" and HandoffBehavior com várias animações  
 Às vezes parece que ignora uma animação seu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade quando ele é substituído por uma segunda animação. Executar o exemplo a seguir, que cria dois <xref:System.Windows.Media.Animation.Storyboard> objetos e usá-los para animar o mesmo <xref:System.Windows.Media.TranslateTransform> mostrado no exemplo anterior.  
  
 A primeira <xref:System.Windows.Media.Animation.Storyboard>, `B1`, anima a <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade o <xref:System.Windows.Media.TranslateTransform> de 0 a 350, que move o retângulo 350 pixels para a direita. Quando a animação atingir o final de sua duração e parar a execução, o <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade será revertido para seu valor original, 0. Como resultado, o retângulo move-se para a direita em 350 pixels e, em seguida, retorna para a sua posição original.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 A segunda <xref:System.Windows.Media.Animation.Storyboard>, `B2`, também anima a <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade do mesmo <xref:System.Windows.Media.TranslateTransform>. Porque somente o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade da animação neste <xref:System.Windows.Media.Animation.Storyboard> está definida, a animação usa o valor atual da propriedade que anima como seu valor inicial.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Se você clicar no botão segundo ao primeiro <xref:System.Windows.Media.Animation.Storyboard> está em execução, você pode esperar o seguinte comportamento:  
  
1.  O primeiro storyboard termina e envia o retângulo de volta para sua posição original, porque a animação tem um <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2.  O segundo storyboard entra em vigor e anima, da posição atual, que agora é 0, até a posição 500.  
  
 **Mas não isso o que acontece.** Em vez disso, o retângulo não retorna, mas continua se movendo para a direita. Isso acontece porque a segunda animação usa o valor atual da primeira animação como seu valor inicial e anima desse valor até o 500. Quando a segunda animação substitui a primeira porque o <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> for usado, o <xref:System.Windows.Media.Animation.FillBehavior> da primeira animação não importa.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior e o evento concluído  
 Os exemplos a seguir demonstram outra situação em que o <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> parece não ter nenhum efeito. Novamente, o exemplo usa um Storyboard para animar a <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade o <xref:System.Windows.Media.TranslateTransform> de 0 a 350. No entanto, dessa vez o exemplo registra para o <xref:System.Windows.Media.Animation.Timeline.Completed> evento.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 O <xref:System.Windows.Media.Animation.Timeline.Completed> manipulador inicia outro <xref:System.Windows.Media.Animation.Storyboard> que anima a mesma propriedade de seu valor atual a 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 A seguir está a marcação que define o segundo <xref:System.Windows.Media.Animation.Storyboard> como um recurso.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Quando você executa o <xref:System.Windows.Media.Animation.Storyboard>, você pode esperar que o <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade do <xref:System.Windows.Media.TranslateTransform> para animar de 0 a 350, em seguida, retornar para 0 após ser concluída (porque ela tem um <xref:System.Windows.Media.Animation.FillBehavior> configuração de <xref:System.Windows.Media.Animation.FillBehavior.Stop>) e, em seguida, animar de 0 a 500. Em vez disso, o <xref:System.Windows.Media.TranslateTransform> anima de 0 a 350 e, em seguida, até 500.  
  
 Isso se deve a ordem na qual [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gera eventos e como os valores de propriedade são armazenados em cache e não são recalculadas, a menos que a propriedade é invalidada. O <xref:System.Windows.Media.Animation.Timeline.Completed> evento é processado primeiro porque ele foi acionado pelo cronograma raiz (o primeiro <xref:System.Windows.Media.Animation.Storyboard>). Neste momento, o <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade ainda retorna seu valor animado porque ele ainda não foi invalidado. O segundo <xref:System.Windows.Media.Animation.Storyboard> usa o valor em cache como seu valor inicial e começa a animação.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Desempenho  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>As animações continuam a ser executadas depois de sair de uma página  
 Quando você navega para fora de um <xref:System.Windows.Controls.Page> que contenha animações em execução, as animações continuarão a ser executadas até que o <xref:System.Windows.Controls.Page> é coletado como lixo. Dependendo do sistema de navegação que você está usando, uma página da qual você sai talvez continue na memória por um tempo indefinido, consumindo recursos com as animações. Isso é mais perceptível quando uma página contém animações em constante execução ("ambiente").  
  
 Por esse motivo, é recomendável usar o <xref:System.Windows.FrameworkElement.Unloaded> evento para remover as animações quando você navegar para fora de uma página.  
  
 Há diferentes maneiras de remover uma animação. As técnicas a seguir podem ser usadas para remover as animações que pertencem a um <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Para remover um <xref:System.Windows.Media.Animation.Storyboard> iniciada com um gatilho de evento, consulte [como: remover um Storyboard](http://msdn.microsoft.com/library/7fe39531-de2f-46a0-a69f-b783d04235ee).  
  
-   Usar código para remover um <xref:System.Windows.Media.Animation.Storyboard>, consulte o <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> método.  
  
 A próxima técnica pode ser usada independentemente de como a animação foi iniciada.  
  
-   Para remover as animações de uma propriedade específica, use o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> método. Especifique a propriedade sendo animada como o primeiro parâmetro, e `null` como o segundo. Isso removerá todos os relógios de animação da propriedade.  
  
 Para obter mais informações sobre as diferentes maneiras para animar propriedades, consulte [visão geral de técnicas de animação de propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>O uso do HandoffBehavior composto consome recursos do sistema  
 Quando você aplica um <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, ou <xref:System.Windows.Media.Animation.AnimationClock> para uma propriedade usando o <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, qualquer <xref:System.Windows.Media.Animation.Clock> objetos anteriormente associados com aquela propriedade continuam a consumir recursos do sistema; o sistema de temporização não será Remova esses relógios automaticamente.  
  
 Para evitar problemas de desempenho ao aplicar um grande número de relógios usando <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, você deve remover relógios de composição da propriedade animada após a conclusão. Há várias maneiras para remover um relógio.  
  
-   Para remover todos os relógios de uma propriedade, use o <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> ou <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> método do objeto animado. Especifique a propriedade sendo animada como o primeiro parâmetro, e `null` como o segundo. Isso removerá todos os relógios de animação da propriedade.  
  
-   Para remover um determinado <xref:System.Windows.Media.Animation.AnimationClock> de uma lista de relógios, use o <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriedade do <xref:System.Windows.Media.Animation.AnimationClock> para recuperar um <xref:System.Windows.Media.Animation.ClockController>, chame o <xref:System.Windows.Media.Animation.ClockController.Remove%2A> método do <xref:System.Windows.Media.Animation.ClockController>. Isso geralmente é feito o <xref:System.Windows.Media.Animation.Clock.Completed> um relógio de manipulador de eventos. Observe que somente relógios de raiz podem ser controlados por um <xref:System.Windows.Media.Animation.ClockController>; o <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriedade de um relógio filho retornará `null`. Observe também que o <xref:System.Windows.Media.Animation.Clock.Completed> evento não será chamado se a duração efetiva do relógio for indefinida.  Nesse caso, o usuário precisará determinar quando chamar <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Isso é basicamente um problema para animações em objetos que têm um longo tempo de vida.  Quando um objeto passa pela coleta de lixo, seus relógios também serão desconectados e coletados como lixo.  
  
 Para obter mais informações sobre objetos clock, consulte [visão geral do sistema de controle de tempo e animação](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
