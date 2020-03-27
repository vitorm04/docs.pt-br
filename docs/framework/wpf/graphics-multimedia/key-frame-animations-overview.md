---
title: Visão geral das animações de quadro-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: 8eb590b07eae3b76b3a206b9731997a6bc2c90d7
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344902"
---
# <a name="key-frame-animations-overview"></a>Visão geral das animações de quadro-chave
Este tópico apresenta as animações de quadro-chave. As animações de quadro-chave permitem realizar animações usando mais de dois valores de destino e controlam o método de interpolação de uma animação.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esta visão geral, você deverá estar familiarizado com as animações e linhas do tempo do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Para obter uma introdução às animações, consulte a [Visão geral da animação](animation-overview.md). Ela também ajuda a se familiarizar com as animações De/Para/Por. Para obter mais informações, consulte a Visão geral das animações De/Para/Por.  
  
<a name="whatisakeyframeanimation"></a>
## <a name="what-is-a-key-frame-animation"></a>O que é uma animação de quadro-chave?  
 Assim como uma animação De/Para/Por, uma animação de quadro-chave anima o valor de uma propriedade de destino. Cria uma transição entre seus <xref:System.Windows.Media.Animation.Timeline.Duration%2A>valores-alvo sobre seus . No entanto, enquanto uma animação De/Para/Por cria uma transição entre dois valores, uma única animação de quadro-chave pode criar transições entre qualquer número de valores de destino. Ao contrário de uma animação De/Para/Por, uma animação de quadro-chave não tem nenhuma propriedade De, Para ou Por com a qual seus valores de destino são definidos. Os valores de destino de uma animação de quadro-chave são descritos com o uso de objetos de quadros-chave (daí o termo “animação de quadro-chave”). Para especificar os valores de destino da animação, você cria <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> objetos de quadro-chave e os adiciona à coleção da animação. Quando a animação é executada, ela faz a transição entre os quadros especificados.  
  
 Além de dar suporte a vários valores de destino, alguns métodos de quadro-chave até mesmo dão suporte a vários métodos de interpolação. O método de interpolação de uma animação define como ela faz a transição de um valor para o próximo. Há três tipos de interpolações: discreta, linear e spline.  
  
 Para realizar uma animação de quadro-chave, conclua as etapas a seguir.  
  
- Declare a animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A>e especifique sua, assim como você faria para uma animação de/para/para/ por.  
  
- Para cada valor-alvo, crie um quadro-chave do <xref:System.Windows.Media.Animation.KeyTime>tipo apropriado, defina <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> seu valor e adicione-o à coleção da animação.  
  
- Associe a animação a uma propriedade, exatamente como você faria com uma animação De/Para/Por. Para obter mais informações sobre como aplicar uma animação a uma propriedade usando um storyboard, consulte [Visão geral dos storyboards](storyboards-overview.md).  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Shapes.Rectangle> um para animar um elemento para quatro locais diferentes.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Como uma animação De/Para/Por, uma animação de quadro-chave pode <xref:System.Windows.Media.Animation.Storyboard> ser aplicada a uma <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> propriedade usando uma marcação e código em uma marcação ou usando o método em código. Você também pode usar uma animação <xref:System.Windows.Media.Animation.AnimationClock> de quadro-chave para criar um e aplicá-lo a uma ou mais propriedades. Para obter mais informações sobre os diferentes métodos para aplicar animações, consulte a visão geral das [técnicas de animação de propriedade](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>
## <a name="key-frame-animation-types"></a>Tipos de animação de quadro-chave  
 Como as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade <xref:System.Double> que toma um (como a propriedade de <xref:System.Windows.FrameworkElement.Width%2A> um <xref:System.Double> elemento), você usa uma animação que produz valores. Para animar uma propriedade <xref:System.Windows.Point>que leva um , <xref:System.Windows.Point> você usa uma animação que produz valores, e assim por diante.  
  
 As classes de animação de <xref:System.Windows.Media.Animation> quadro-chave pertencem ao namespace e aderem à seguinte convenção de nomeação:  
  
 * \<Digite>*`AnimationUsingKeyFrames`  
  
 Onde * \<o tipo>* é o tipo de valor que a classe anima.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece as classes de animação de quadro-chave a seguir.  
  
|Tipo de propriedade|Classe de animação De/Para/Por correspondente|Métodos de interpolação com suporte|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Discreto|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Discreto|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Discreto|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Discreto|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Discreto, linear, spline|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Discreto, linear, spline|  
  
<a name="animation_target_values"></a>
## <a name="target-values-key-frames-and-key-times"></a>Valores de destino (quadros-chave) e tempos-chave  
 Assim como há diferentes tipos de animações de quadro-chave para animar diferentes tipos de propriedades, também existem diferentes tipos de objetos de quadro-chave: um para cada tipo de valor animado e o método de interpolação com suporte. Os tipos de quadro-chave seguem esta convenção de nomenclatura:  
  
 *InterpolaçãoMétodo \<>tipo>\<*`KeyFrame`  
  
 Quando * \<InterpolationMethod>* é o método de interpolação que o quadro-chave usa e * \<type>* é o tipo de valor que a classe anima. Uma animação de quadro-chave que dá suporte aos três métodos de interpolação terá três tipos de quadro-chave que podem ser usados. Por exemplo, você pode usar três <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>tipos <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>de <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>quadros-chave com: , e . (Os métodos de interpolação são descritos detalhadamente em uma seção posterior.)  
  
 O objetivo principal de um quadro-chave é especificar a <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> e a <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Cada tipo de quadro-chave fornece essas duas propriedades.  
  
- A <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriedade especifica o valor-alvo para esse quadro-chave.  
  
- A <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriedade especifica quando (dentro <xref:System.Windows.Media.Animation.Timeline.Duration%2A>da animação) um <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> quadro-chave é alcançado.  
  
 Quando uma animação de quadro-chave começa, itera através de <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> seus quadros-chave na ordem definida por suas propriedades.  
  
- Se não houver quadro-chave no momento 0, a animação criará uma <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> transição entre o valor atual da propriedade-alvo e o do primeiro quadro-chave; caso contrário, o valor de saída da animação torna-se o valor do primeiro quadro-chave.  
  
- A animação cria uma <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> transição entre o primeiro e o segundo quadros-chave usando o método de interpolação especificado pelo segundo quadro-chave. A transição começa no primeiro <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> quadro-chave e termina <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> quando o segundo quadro-chave é alcançado.  
  
- A animação continua, criando transições entre cada próximo quadro-chave e seu quadro-chave anterior.  
  
- Finalmente, a animação passa para o valor do quadro-chave com o maior tempo-chave <xref:System.Windows.Media.Animation.Timeline.Duration%2A>que é igual ou menor que o da animação .  
  
 Se a animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Duration.Automatic%2A> é <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ou sua é igual à hora do último quadro-chave, a animação termina. Caso contrário, se a <xref:System.Windows.Duration> animação for maior que o tempo-chave do último quadro-chave, a animação <xref:System.Windows.Duration>mantém o valor do quadro-chave até chegar ao final de sua . Como todas as animações, uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> animação de quadro-chave usa sua propriedade para determinar se ela mantém seu valor final quando chega ao final de seu período ativo. Para obter mais informações, consulte a [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md).  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> seguir usa o objeto definido <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> no exemplo anterior para demonstrar como as propriedades funcionam.  
  
- O primeiro quadro-chave define imediatamente o valor de saída da animação como 0.  
  
- O segundo quadro-chave é animado de 0 a 350. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 0 segundo) e é reproduzido por 2 segundos, sendo encerrado no tempo = 0:0:2.  
  
- O terceiro quadro-chave é animado de 350 a 50. Ele é iniciado após o término do segundo quadro-chave (no tempo = 2 segundos) e é reproduzido por 5 segundos, sendo encerrado no tempo = 0:0:7.  
  
- O quarto quadro-chave é animado de 50 a 200. Ele é iniciado após o término do terceiro quadro-chave (no tempo = 7 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:8.  
  
- Como <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a propriedade da animação foi definida para 10 segundos, a animação mantém seu valor final por dois segundos antes de terminar no tempo = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>
## <a name="interpolation-methods"></a>Métodos de interpolação  
 As seções anteriores mencionaram que algumas animações de quadro-chave dão suporte a vários métodos de interpolação. A interpolação de uma animação descreve como uma animação faz a transição entre valores ao longo de sua duração. Ao selecionar o tipo de quadro-chave usado na animação, você poderá definir o método de interpolação para esse segmento de quadro-chave. Há três tipos de métodos de interpolação diferentes: linear, discreto e spline.  
  
### <a name="linear-interpolation"></a>Interpolação linear  
 Com a interpolação linear, a animação progride a uma taxa constante da duração do segmento. Por exemplo, se um segmento de quadro-chave fizer a transição de 0 a 10 em uma duração de 5 segundos, a animação gerará os seguintes valores nos tempos especificados:  
  
|Hora|Valor de saída|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>Interpolação discreta  
 Com a interpolação discreta, a função de animação salta de um valor para o próximo sem interpolação. Se um segmento de quadro-chave fizer a transição de 0 a 10 em uma duração de 5 segundos, a animação gerará os seguintes valores nos tempos especificados:  
  
|Hora|Valor de saída|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 Observe como a animação não altera seu valor de saída até exatamente o final da duração do segmento.  
  
 A interpolação spline é mais complexa. Ela é descrita na próxima seção.  
  
<a name="anim_spline"></a>
### <a name="splined-interpolation"></a>Interpolação spline  
 A interpolação spline pode ser usada para obter efeitos de tempo mais realistas. Como as animações costumam ser usadas para imitar efeitos que ocorrem no mundo real, os desenvolvedores podem precisar de um controle refinado sobre a aceleração e desaceleração de objetos e uma manipulação minuciosa dos segmentos de tempo. Os quadros-chave spline permitem realizar animações com interpolação spline. Com outros quadros-chave, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>você especifica um e . Com um quadro-chave spline, <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>você também especifica um . O exemplo a seguir mostra um <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>único quadro de chave spline para um . Observe <xref:System.Windows.Media.Animation.KeySpline> a propriedade; isso é o que torna um quadro de chave spline diferente dos outros tipos de quadros-chave.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Uma curva de Bézier cúbica é definida por um ponto inicial, um ponto final e dois pontos de controle. A <xref:System.Windows.Media.Animation.KeySpline> propriedade de um quadro-chave spline define os dois pontos de controle de uma curva de Bezier que se estende de (0,0) a (1,1). O primeiro ponto de controle controla o fator de curva da primeira metade da curva de Bézier e o segundo ponto de controle controla o fator de curva da segunda metade do segmento de Bézier. A curva resultante descreve a taxa de alteração desse quadro-chave spline. Quanto mais íngreme for a curva, mais rápido o quadro-chave mudará seus valores. Conforme a curva fica mais plana, o quadro-chave muda seus valores mais lentamente.  
  
 Você pode <xref:System.Windows.Media.Animation.KeySpline> usar para simular trajetórias físicas como água caindo ou bolas saltando, ou aplicar outros efeitos de "facilidade" e "facilidade" para animações de movimento. Para efeitos de interação do usuário como esmaecimento da tela de fundo ou reassociação do botão de controle, você poderá aplicar a interpolação spline para acelerar ou diminuir a taxa de alteração de uma animação de uma maneira específica.  
  
 O exemplo a <xref:System.Windows.Media.Animation.KeySpline> seguir especifica um de 0,1 1 1,0, que cria a seguinte curva bezier.  
  
 ![Uma curva de Bézier](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Um spline-chave com pontos de controle (0,0, 1,0) e (1,0, 0,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Esse quadro-chave é animado rapidamente quando é iniciado, desacelera e, em seguida, acelera novamente antes de ser encerrado.  
  
 O exemplo a <xref:System.Windows.Media.Animation.KeySpline> seguir especifica uma de 0,5,0,25 0,75,1.0, que cria a seguinte curva de Bezier.  
  
 ![Uma curva de Bézier](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Um spline-chave com pontos de controle (0,25, 0,5) e (0,75, 1,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Como a curvatura da curva de Bézier muda muito pouco, esse quadro-chave é animado a uma taxa quase constante; ele desacelera um pouco quase no final.  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> seguir usa um para animar a posição do retângulo. Como <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> os <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> objetos de uso, a transição entre cada valor de quadro-chave usa interpolação splined.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 A interpolação spline pode ser difícil de entender; pode ser útil testar diferentes configurações. A [Amostra de animação de spline-chave](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations) permite alterar os valores do spline-chave e ver o resultado na animação.  
  
<a name="combininginterpolationmethods"></a>
### <a name="combining-interpolation-methods"></a>Combinando métodos de interpolação  
 É possível usar quadros-chave com diferentes tipos de interpolação em uma única animação de quadro-chave. Quando duas animações de quadro-chave com diferentes interpolações ocorrem uma após a outra, o método de interpolação do segundo quadro-chave é usado para criar a transição do primeiro valor para o segundo.  
  
 No exemplo a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> seguir, é criado um que usa interpolação linear, esvestida e discreta.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>
## <a name="more-about-duration-and-key-times"></a>Mais informações sobre duração e tempos-chave  
 Como outras animações, as animações de quadro-chave têm uma <xref:System.Windows.Duration> propriedade. Além de especificar a <xref:System.Windows.Duration>animação, você precisa especificar qual parte dessa duração é dada a cada quadro de tecla. Você faz isso descrevendo <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> um para cada um dos quadros-chave da animação. Cada quadro da <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> chave especifica quando esse quadro-chave termina.  
  
 A <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriedade não especifica quanto tempo o tempo-chave é reproduzido. O tempo durante o qual um quadro-chave é reproduzido é determinado pelo tempo em que o quadro-chave é encerrado, pelo tempo em que o quadro-chave anterior foi encerrado e pela duração da animação. Os tempos-chave podem ser especificados como um valor <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> de <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>tempo, uma porcentagem ou como valores especiais ou .  
  
 A lista a seguir descreve as diferentes maneiras de especificar os tempos-chave.  
  
### <a name="timespan-values"></a>Valores TimeSpan  
 Você pode <xref:System.TimeSpan> usar valores para especificar um <xref:System.Windows.Media.Animation.KeyTime>. O valor deve ser maior ou igual a 0 e menor ou igual à duração da animação. O exemplo a seguir mostra uma animação com uma duração de 10 segundos e quatro quadros-chave cujos tempos-chave são especificados como valores temporais.  
  
- O primeiro quadro-chave é animado do valor base para 100 durante os primeiros 3 segundos, sendo encerrado no tempo = 0:0:03.  
  
- O segundo quadro-chave é animado de 100 a 200. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 3 segundos) e é reproduzido por 5 segundos, sendo encerrado no tempo = 0:0:8.  
  
- O terceiro quadro-chave é animado de 200 a 500. Ele é iniciado após o término do segundo quadro-chave (no tempo = 8 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:9.  
  
- O quarto quadro-chave é animado de 500 a 600. Ele é iniciado após o término do terceiro quadro-chave (no tempo = 9 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Valores percentuais  
 Um valor percentual especifica que o quadro-chave termina <xref:System.Windows.Media.Animation.Timeline.Duration%2A>em alguma porcentagem da animação . No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você especifica o percentual como um número seguido pelo símbolo `%`. Em código, você <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> usa o <xref:System.Double> método e passa-o indicando a porcentagem. O valor deve ser maior ou igual a 0 e menor ou igual a 100%. O exemplo a seguir mostra uma animação com uma duração de 10 segundos e quatro quadros-chave cujos tempos-chave são especificados como percentuais.  
  
- O primeiro quadro-chave é animado do valor base para 100 durante os primeiros 3 segundos, sendo encerrado no tempo = 0:0:3.  
  
- O segundo quadro-chave é animado de 100 a 200. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 3 segundos) e é reproduzido por 5 segundos, sendo encerrado no tempo = 0:0:8 (0,8 * 10 = 8).  
  
- O terceiro quadro-chave é animado de 200 a 500. Ele é iniciado após o término do segundo quadro-chave (no tempo = 8 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:9 (0,9 * 10 = 9).  
  
- O quarto quadro-chave é animado de 500 a 600. Ele é iniciado após o término do terceiro quadro-chave (no tempo = 9 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Valor especial, uniforme  
 Use <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> o tempo quando quiser que cada quadro de tecla demora a mesma quantidade de tempo.  
  
 Um <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> tempo-chave divide o tempo disponível igualmente pelo número de quadros-chave para determinar o tempo final de cada quadro de tecla. O exemplo a seguir mostra uma animação com duração de 10 segundos <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>e quatro quadros-chave cujos tempos-chave são especificados como .  
  
- O primeiro quadro-chave é animado do valor base para 100 durante os primeiros 2,5 segundos, sendo encerrado no tempo = 0:0:2.5.  
  
- O segundo quadro-chave é animado de 100 a 200. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 2,5 segundos) e é reproduzido por aproximadamente 2,5 segundos, sendo encerrado no tempo = 0:0:5.  
  
- O terceiro quadro-chave é animado de 200 a 500. Ele é iniciado após o término do segundo quadro-chave (no tempo = 5 segundos) e é reproduzido por 2,5 segundos, sendo encerrado no tempo = 0:0:7.5.  
  
- O quarto quadro-chave é animado de 500 a 600. Ele é iniciado após o término do segundo quadro-chave (no tempo = 7,5 segundos) e é reproduzido por 2,5 segundos, sendo encerrado no tempo = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Valor especial, personalizado  
 Use <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> o tempo quando quiser se animar a um ritmo constante.  
  
 Um <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> tempo-chave aloca o tempo disponível de acordo com o comprimento de cada um dos quadros-chave para determinar a duração de cada quadro.  Isso fornecerá o comportamento em que a velocidade ou o ritmo da animação permanece constante.  O exemplo a seguir mostra uma animação com duração de 10 segundos <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>e três quadros-chave cujos tempos-chave são especificados como .  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Observe que, se o tempo-chave <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> do <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>último quadro-chave for ou , seu tempo-chave resolvido será definido como 100%. Se o primeiro quadro-chave em uma animação com vários quadros for personalizado, seu tempo-chave resolvido será definido como 0. (Se a coleção de quadros-chave contiver apenas um único quadro-chave e ele for um quadro-chave personalizado, seu tempo-chave resolvido será definido como 100%.)  
  
 Diferentes quadros-chave em uma animação de quadro-chave único podem usar diferentes tipos de tempos-chave.  
  
<a name="combiningkeytimes"></a>
## <a name="combining-key-times-out-of-order-key-frames"></a>Combinando tempos-chave e quadros-chave fora de ordem  
 Você pode usar quadros-chave com diferentes <xref:System.Windows.Media.Animation.KeyTime> tipos de valor na mesma animação. E, embora seja recomendável adicionar quadros-chave na ordem em que eles devem ser reproduzidos, isso não é necessário. O sistema de animação e tempo pode resolver quadros-chave fora de ordem. Os quadros-chave com tempos-chave inválidos são ignorados.  
  
 A lista a seguir descreve o procedimento pelo qual os tempos-chave são resolvidos para os quadros-chave de uma animação de quadro-chave.  
  
1. Resolver <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> valores.  
  
2. Determine o *tempo total de interpolação* da animação, o tempo total necessário para que a animação de quadro-chave conclua uma interação progressiva.  
  
    1. Se a animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A> não <xref:System.Windows.Duration.Automatic%2A> <xref:System.Windows.Duration.Forever%2A>for ou , o tempo total de <xref:System.Windows.Media.Animation.Timeline.Duration%2A> interpolação é o valor da propriedade da animação.  
  
    2. Caso contrário, o tempo total <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> de interpolação é o maior valor especificado entre seus quadros-chave, se existiralgum.  
  
    3. Caso contrário, o tempo total de interpolação será de 1 segundo.  
  
3. Use o valor total do <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> tempo de interpolação para resolver valores.  
  
4. Resolva o último quadro-chave, caso ele ainda não tenha sido resolvido nas etapas anteriores. Se <xref:System.Windows.Media.Animation.KeyTime> o último quadro-chave for <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, seu tempo resolvido será igual ao tempo total de interpolação.  
  
     Se <xref:System.Windows.Media.Animation.KeyTime> o primeiro quadro-chave for <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> e esta animação tiver mais <xref:System.Windows.Media.Animation.KeyTime> do que em quadros-chave, resolva seu valor a zero; se houver apenas um quadro-chave e seu <xref:System.Windows.Media.Animation.KeyTime> valor for, <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>ele está resolvido para o tempo total de interpolação, conforme descrito na etapa anterior.  
  
5. Resolver <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> os valores restantes: cada um deles recebe uma parte igual do tempo disponível.  Durante esse processo, <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> os valores <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> não resolvidos são tratados temporariamente como valores e recebem um tempo temporário de resolução.  
  
6. Resolva <xref:System.Windows.Media.Animation.KeyTime> os valores dos quadros-chave com tempos-chave não especificados <xref:System.Windows.Media.Animation.KeyTime> usando os quadros-chave declarados mais próximos a eles que tenham valores resolvidos.  
  
7. Resolva <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> os valores restantes. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> use <xref:System.Windows.Media.Animation.KeyTime> os valores dos quadros-chave vizinhos para determinar seu tempo resolvido.  O objetivo é garantir que a velocidade da animação é constante em relação ao tempo resolvido desse quadro-chave.  
  
8. Classificar quadros-chave por ordem de tempo resolvido (chave primária) e ordem de declaração (chave secundária), <xref:System.Windows.Media.Animation.KeyTime> ou seja, usar um tipo estável com base nos valores de quadro de chave resolvidos.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Amostra de animação de spline-chave](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)
- [Amostra de animação de KeyFrame](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)
- [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md)
