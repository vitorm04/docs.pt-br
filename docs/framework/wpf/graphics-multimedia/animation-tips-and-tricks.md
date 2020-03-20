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
ms.openlocfilehash: 6b540448599c1e1083ed367a312ef60fceacd0d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187644"
---
# <a name="animation-tips-and-tricks"></a>Dicas e truques de animação
Ao trabalhar com animações no WPF, existem uma série de dicas e truques que podem fazer suas animações funcionarem melhor e salvar sua frustração.  
  
<a name="generalissuessection"></a>
## <a name="general-issues"></a>Problemas gerais  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animar a posição de uma barra de rolagem ou controle deslizante os deixa congelados  
 Se você animar a posição de uma barra de rolagem ou controle deslizante usando uma animação que tenha um <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (o valor padrão), o usuário não poderá mais mover a barra de rolagem ou o controle deslizante. Isso acontece porque, mesmo que a animação tenha terminado, ela ainda estará substituindo o valor base da propriedade de destino. Para impedir que a animação sobrepor o valor atual da <xref:System.Windows.Media.Animation.FillBehavior> propriedade, remova-a ou dê-lhe um de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Para obter mais informações e um exemplo, consulte [Definir uma propriedade depois de animá-la com um Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animar a saída de uma animação não tem nenhum efeito  
 Você não pode animar um objeto que é a saída de outra animação. Por exemplo, se <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> você usa <xref:System.Windows.Shapes.Shape.Fill%2A> um <xref:System.Windows.Shapes.Rectangle> para <xref:System.Windows.Media.RadialGradientBrush> animar <xref:System.Windows.Media.SolidColorBrush>o de a a, você <xref:System.Windows.Media.RadialGradientBrush> não <xref:System.Windows.Media.SolidColorBrush>pode animar quaisquer propriedades do ou .  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Não é possível alterar o valor de uma propriedade após animá-la  
 Em alguns casos, pode parecer que não é possível alterar o valor de uma propriedade depois de ela ter sido animada, mesmo após o término da animação. Isso acontece porque, mesmo que a animação tenha terminado, ela ainda estará substituindo o valor base da propriedade. Para impedir que a animação sobrepor o valor atual da <xref:System.Windows.Media.Animation.FillBehavior> propriedade, remova-a ou dê-lhe um de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Para obter mais informações e um exemplo, consulte [Definir uma propriedade depois de animá-la com um Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Alterar uma linha do tempo não tem nenhum efeito  
 Embora <xref:System.Windows.Media.Animation.Timeline> a maioria das propriedades sejam animatable e possam <xref:System.Windows.Media.Animation.Timeline> ser vinculadas a dados, alterar os valores de propriedade de um ativo parece não ter efeito. Isso porque, quando <xref:System.Windows.Media.Animation.Timeline> um é iniciado, o sistema <xref:System.Windows.Media.Animation.Timeline> de cronometragem faz <xref:System.Windows.Media.Animation.Clock> uma cópia do e usa-o para criar um objeto. Modificar o original não causa nenhum efeito na cópia do sistema.  
  
 Para <xref:System.Windows.Media.Animation.Timeline> refletir as mudanças, seu relógio deve ser regenerado e usado para substituir o relógio previamente criado. Os relógios não são regenerados automaticamente para você. A seguir estão várias maneiras para aplicar alterações de linha do tempo:  
  
- Se a linha do <xref:System.Windows.Media.Animation.Storyboard>tempo é ou pertence a um , você <xref:System.Windows.Media.Animation.BeginStoryboard> pode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> fazê-lo refletir mudanças reaplicando seu storyboard usando um ou o método. Isso tem o efeito colateral de também reiniciar a animação. Em código, você <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> pode usar o método para avançar o storyboard de volta à sua posição anterior.  
  
- Se você aplicou uma animação diretamente <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> a uma <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> propriedade usando o método, chame o método novamente e passe-o pela animação que foi modificada.  
  
- Se você estiver trabalhando diretamente no nível do relógio, crie e aplique um novo conjunto de relógios e use-os para substituir o conjunto anterior de relógios gerados.  
  
 Para obter mais informações sobre cronogramas e relógios, consulte [Visão geral do sistema de animação e tempo](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>O FillBehavior.Stop não funciona como o esperado  
 Há momentos em <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> que <xref:System.Windows.Media.Animation.FillBehavior.Stop> a configuração da propriedade parece não ter efeito, como <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> quando <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>uma animação "entrega" para outra porque tem uma configuração de .  
  
 O exemplo a <xref:System.Windows.Controls.Canvas>seguir <xref:System.Windows.Shapes.Rectangle> cria <xref:System.Windows.Media.TranslateTransform>um , a e a . O <xref:System.Windows.Media.TranslateTransform> será animado para <xref:System.Windows.Shapes.Rectangle> mover <xref:System.Windows.Controls.Canvas>o redor do .  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Os exemplos nesta seção usam os objetos <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> anteriores para demonstrar vários casos em que a propriedade não se comporta como você poderia esperar.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" and HandoffBehavior com várias animações  
 Às vezes parece que uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> animação ignora sua propriedade quando é substituída por uma segunda animação. Tome-se o exemplo <xref:System.Windows.Media.Animation.Storyboard> a seguir, que cria <xref:System.Windows.Media.TranslateTransform> dois objetos e os usa para animar o mesmo mostrado no exemplo anterior.  
  
 O <xref:System.Windows.Media.Animation.Storyboard>primeiro `B1`, anima <xref:System.Windows.Media.TranslateTransform.X%2A> a propriedade <xref:System.Windows.Media.TranslateTransform> do 0 a 350, que move o retângulo de 350 pixels para a direita. Quando a animação chega ao fim de sua <xref:System.Windows.Media.TranslateTransform.X%2A> duração e para de tocar, a propriedade reverte para seu valor original, 0. Como resultado, o retângulo move-se para a direita em 350 pixels e, em seguida, retorna para a sua posição original.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 O <xref:System.Windows.Media.Animation.Storyboard>segundo `B2`, também anima <xref:System.Windows.Media.TranslateTransform.X%2A> a propriedade <xref:System.Windows.Media.TranslateTransform>do mesmo. Como apenas <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> a propriedade da <xref:System.Windows.Media.Animation.Storyboard> animação neste conjunto é definida, a animação usa o valor atual da propriedade que ele anima como seu valor inicial.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Se você clicar no segundo <xref:System.Windows.Media.Animation.Storyboard> botão enquanto o primeiro estiver sendo reproduzido, você pode esperar o seguinte comportamento:  
  
1. O primeiro storyboard termina e envia o retângulo de volta <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.Stop>à sua posição original, porque a animação tem um de .  
  
2. O segundo storyboard entra em vigor e anima, da posição atual, que agora é 0, até a posição 500.  
  
 **Mas não isso o que acontece.** Em vez disso, o retângulo não retorna, mas continua se movendo para a direita. Isso acontece porque a segunda animação usa o valor atual da primeira animação como seu valor inicial e anima desse valor até o 500. Quando a segunda animação substitui <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> a primeira <xref:System.Windows.Media.Animation.FillBehavior> porque é usada, a da primeira animação não importa.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior e o evento concluído  
 Os exemplos seguintes demonstram outro <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> cenário em que parece não ter efeito. Novamente, o exemplo usa um Storyboard para animar a <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade <xref:System.Windows.Media.TranslateTransform> do 0 a 350. No entanto, desta vez <xref:System.Windows.Media.Animation.Timeline.Completed> o exemplo se inscreve para o evento.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 O <xref:System.Windows.Media.Animation.Timeline.Completed> manipulador de <xref:System.Windows.Media.Animation.Storyboard> eventos inicia outro que anima a mesma propriedade de seu valor atual para 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 A seguir está a marcação <xref:System.Windows.Media.Animation.Storyboard> que define o segundo como um recurso.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Quando você <xref:System.Windows.Media.Animation.Storyboard>executa o <xref:System.Windows.Media.TranslateTransform.X%2A> , você <xref:System.Windows.Media.TranslateTransform> pode esperar a propriedade do para animar de 0 a 350, em seguida, reverter para 0 depois que ele completa (porque tem um <xref:System.Windows.Media.Animation.FillBehavior> ajuste de <xref:System.Windows.Media.Animation.FillBehavior.Stop>), e depois animar de 0 a 500. Em vez <xref:System.Windows.Media.TranslateTransform> disso, os animade de 0 a 350 e depois para 500.  
  
 Isso é por causa da ordem em que o WPF levanta eventos e porque os valores da propriedade são armazenados em cache e não são recalculados a menos que a propriedade seja invalidada. O <xref:System.Windows.Media.Animation.Timeline.Completed> evento é processado primeiro porque foi acionado pela <xref:System.Windows.Media.Animation.Storyboard>linha do tempo raiz (a primeira ). Neste momento, <xref:System.Windows.Media.TranslateTransform.X%2A> a propriedade ainda devolve seu valor animado porque ainda não foi invalidado. O <xref:System.Windows.Media.Animation.Storyboard> segundo usa o valor armazenado como seu valor inicial e começa a animar.  
  
<a name="performancesection"></a>
## <a name="performance"></a>Desempenho  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>As animações continuam a ser executadas depois de sair de uma página  
 Quando você navegar <xref:System.Windows.Controls.Page> para longe de um que contém animações <xref:System.Windows.Controls.Page> em execução, essas animações continuarão a ser retonadas até que o lixo seja coletado. Dependendo do sistema de navegação que você está usando, uma página da qual você sai talvez continue na memória por um tempo indefinido, consumindo recursos com as animações. Isso é mais perceptível quando uma página contém animações em constante execução ("ambiente").  
  
 Por essa razão, é uma boa <xref:System.Windows.FrameworkElement.Unloaded> ideia usar o evento para remover animações quando você navega para longe de uma página.  
  
 Há diferentes maneiras de remover uma animação. As seguintes técnicas podem ser usadas <xref:System.Windows.Media.Animation.Storyboard>para remover animações que pertencem a um .  
  
- Para remover <xref:System.Windows.Media.Animation.Storyboard> um que você começou com um gatilho de evento, consulte [Como: Remover um Storyboard](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Para usar o <xref:System.Windows.Media.Animation.Storyboard>código para <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> remover um, consulte o método.  
  
 A próxima técnica pode ser usada independentemente de como a animação foi iniciada.  
  
- Para remover animações de uma <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> propriedade específica, use o método. Especifique a propriedade sendo animada `null` como o primeiro parâmetro, e como o segundo. Isso removerá todos os relógios de animação da propriedade.  
  
 Para obter mais informações sobre as diferentes maneiras de animar propriedades, consulte [Visão geral das técnicas de animação de propriedade](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>O uso do HandoffBehavior composto consome recursos do sistema  
 Quando você <xref:System.Windows.Media.Animation.Storyboard>aplica <xref:System.Windows.Media.Animation.AnimationTimeline>um <xref:System.Windows.Media.Animation.AnimationClock> , ou <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>a <xref:System.Windows.Media.Animation.Clock> uma propriedade usando o , quaisquer objetos anteriormente associados a essa propriedade continuam a consumir recursos do sistema; o sistema de cronometragem não removerá esses relógios automaticamente.  
  
 Para evitar problemas de desempenho quando você <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>aplica um grande número de relógios usando, você deve remover relógios de composição da propriedade animada após a conclusão. Há várias maneiras para remover um relógio.  
  
- Para remover todos os relógios <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> de <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> uma propriedade, use o método ou método do objeto animado. Especifique a propriedade sendo animada `null` como o primeiro parâmetro, e como o segundo. Isso removerá todos os relógios de animação da propriedade.  
  
- Para remover <xref:System.Windows.Media.Animation.AnimationClock> um específico de uma lista <xref:System.Windows.Media.Animation.Clock.Controller%2A> de <xref:System.Windows.Media.Animation.AnimationClock> relógios, <xref:System.Windows.Media.Animation.ClockController>use a <xref:System.Windows.Media.Animation.ClockController.Remove%2A> propriedade <xref:System.Windows.Media.Animation.ClockController>do para recuperar um, em seguida, chame o método do . Isso é normalmente <xref:System.Windows.Media.Animation.Clock.Completed> feito no manipulador de eventos para um relógio. Note que apenas relógios raiz <xref:System.Windows.Media.Animation.ClockController>podem ser controlados por um; a <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriedade de um `null`relógio infantil vai voltar. Observe também <xref:System.Windows.Media.Animation.Clock.Completed> que o evento não será chamado se a duração efetiva do relógio for para sempre.  Nesse caso, o usuário precisará determinar <xref:System.Windows.Media.Animation.ClockController.Remove%2A>quando ligar .  
  
 Isso é basicamente um problema para animações em objetos que têm um longo tempo de vida.  Quando um objeto passa pela coleta de lixo, seus relógios também serão desconectados e coletados como lixo.  
  
 Para obter mais informações sobre objetos de relógio, consulte [Visão geral do sistema de animação e tempo](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
