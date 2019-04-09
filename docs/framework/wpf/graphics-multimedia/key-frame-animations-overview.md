---
title: Visão geral das animações de quadro-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: caad7d5694139729ebe89e686ea70a981a0a94d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191575"
---
# <a name="key-frame-animations-overview"></a>Visão geral das animações de quadro-chave
Este tópico apresenta as animações de quadro-chave. As animações de quadro-chave permitem realizar animações usando mais de dois valores de destino e controlam o método de interpolação de uma animação.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esta visão geral, você deverá estar familiarizado com as animações e linhas do tempo do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Para obter uma introdução às animações, consulte a [Visão geral da animação](animation-overview.md). Ela também ajuda a se familiarizar com as animações De/Para/Por. Para obter mais informações, consulte a Visão geral das animações De/Para/Por.  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>O que é uma animação de quadro-chave?  
 Assim como uma animação De/Para/Por, uma animação de quadro-chave anima o valor de uma propriedade de destino. Ele cria uma transição entre seus valores de destino por seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. No entanto, enquanto uma animação De/Para/Por cria uma transição entre dois valores, uma única animação de quadro-chave pode criar transições entre qualquer número de valores de destino. Ao contrário de uma animação De/Para/Por, uma animação de quadro-chave não tem nenhuma propriedade De, Para ou Por com a qual seus valores de destino são definidos. Os valores de destino de uma animação de quadro-chave são descritos com o uso de objetos de quadros-chave (daí o termo “animação de quadro-chave”). Para especificar valores de destino da animação, você cria objetos de quadro-chave e adicioná-los para a animação <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> coleção. Quando a animação é executada, ela faz a transição entre os quadros especificados.  
  
 Além de dar suporte a vários valores de destino, alguns métodos de quadro-chave até mesmo dão suporte a vários métodos de interpolação. O método de interpolação de uma animação define como ela faz a transição de um valor para o próximo. Há três tipos de interpolações: discreta, linear e spline.  
  
 Para realizar uma animação de quadro-chave, conclua as etapas a seguir.  
  
-   Declare a animação e especifique seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, exatamente como você faria para uma animação de/para/por.  
  
-   Para cada valor de destino, crie um quadro-chave do tipo apropriado, defina seu valor e <xref:System.Windows.Media.Animation.KeyTime>e adicioná-lo para a animação <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> coleção.  
  
-   Associe a animação a uma propriedade, exatamente como você faria com uma animação De/Para/Por. Para obter mais informações sobre como aplicar uma animação a uma propriedade usando um storyboard, consulte [Visão geral dos storyboards](storyboards-overview.md).  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animar uma <xref:System.Windows.Shapes.Rectangle> elemento para quatro locais diferentes.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Como um de/para/por animação, uma animação de quadro-chave pode ser aplicada a uma propriedade usando um <xref:System.Windows.Media.Animation.Storyboard> na marcação e código ou usando o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método no código. Você também pode usar uma animação de quadro-chave para criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-lo a uma ou mais propriedades. Para obter mais informações sobre os diferentes métodos para aplicação de animações, consulte a [Visão geral das técnicas de animação de propriedades](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>Tipos de animação de quadro-chave  
 Como as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade que utiliza um <xref:System.Double> (como um elemento <xref:System.Windows.FrameworkElement.Width%2A> propriedade), use uma animação que produz <xref:System.Double> valores. Para animar uma propriedade que utiliza um <xref:System.Windows.Point>, use uma animação que produz <xref:System.Windows.Point> valores e assim por diante.  
  
 As classes de animação de quadro-chave pertencem ao <xref:System.Windows.Media.Animation> namespace e seguem Esta convenção de nomenclatura:  
  
 *\<tipo >* `AnimationUsingKeyFrames`  
  
 Em que *\<Type>* é o tipo de valor animado pela classe.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Fornece as seguintes classes de animação de quadro-chave.  
  
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
  
 *\<InterpolationMethod>\<Type>* `KeyFrame`  
  
 Em que *\<InterpolationMethod>* é o método de interpolação usado pelo quadro-chave e *\<Type>* é o tipo de valor animado pela classe. Uma animação de quadro-chave que dá suporte aos três métodos de interpolação terá três tipos de quadro-chave que podem ser usados. Por exemplo, você pode usar três tipos de quadro-chave com um <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, e <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>. (Os métodos de interpolação são descritos detalhadamente em uma seção posterior.)  
  
 O objetivo principal de um quadro-chave é especificar um <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> e um <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Cada tipo de quadro-chave fornece essas duas propriedades.  
  
-   O <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriedade especifica o valor de destino para o quadro chave.  
  
-   O <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriedade especifica quando (dentro da animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) um quadro chave <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> for atingido.  
  
 Quando uma animação de quadro-chave é iniciada, itera por meio de seus quadros chave na ordem definida por seus <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriedades.  
  
-   Se não houver nenhum quadro-chave no tempo 0, a animação cria uma transição entre o valor atual da propriedade de destino e o <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> do primeiro quadro chave; caso contrário, a saída da animação valor torna-se o valor do primeiro quadro-chave.  
  
-   A animação cria uma transição entre o <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> primeiro e o segundo quadro chave usando o método de interpolação especificado pelo segundo quadro-chave. A transição começa com o primeiro quadro chave <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> e termina quando o segundo quadro chave <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> for atingido.  
  
-   A animação continua, criando transições entre cada próximo quadro-chave e seu quadro-chave anterior.  
  
-   Por fim, a animação faz a transição para o valor do quadro chave com o maior tempo-chave que é igual ou menor do que a animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 Se a animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A> está <xref:System.Windows.Duration.Automatic%2A> ou seu <xref:System.Windows.Media.Animation.Timeline.Duration%2A> é igual à hora do último quadro chave, a animação termina. Caso contrário, se a animação <xref:System.Windows.Duration> é maior que o tempo-chave do último quadro chave, a animação mantém o valor de quadro-chave até que ele atinge o final de seu <xref:System.Windows.Duration>. Assim como todas as animações, uma animação de quadro-chave usa sua <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade para determinar se ela manterá o valor final quando atingir o final do seu período ativo. Para obter mais informações, consulte a [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md).  
  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> objeto definido no exemplo anterior para demonstrar como o <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> e <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> das propriedades.  
  
-   O primeiro quadro-chave define imediatamente o valor de saída da animação como 0.  
  
-   O segundo quadro-chave é animado de 0 a 350. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 0 segundo) e é reproduzido por 2 segundos, sendo encerrado no tempo = 0:0:2.  
  
-   O terceiro quadro-chave é animado de 350 a 50. Ele é iniciado após o término do segundo quadro-chave (no tempo = 2 segundos) e é reproduzido por 5 segundos, sendo encerrado no tempo = 0:0:7.  
  
-   O quarto quadro-chave é animado de 50 a 200. Ele é iniciado após o término do terceiro quadro-chave (no tempo = 7 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:8.  
  
-   Porque o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade da animação foi definida como 10 segundos, a animação mantém seu valor final por dois segundos antes de terminar no tempo = 0:0:10.  
  
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
 A interpolação spline pode ser usada para obter efeitos de tempo mais realistas. Como as animações costumam ser usadas para imitar efeitos que ocorrem no mundo real, os desenvolvedores podem precisar de um controle refinado sobre a aceleração e desaceleração de objetos e uma manipulação minuciosa dos segmentos de tempo. Os quadros-chave spline permitem realizar animações com interpolação spline. Outros quadros chave, você deve especificar uma <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> e <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. Com um quadro-chave spline, você também especificar um <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. O exemplo a seguir mostra um quadro-chave spline único para um <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Observe que o <xref:System.Windows.Media.Animation.KeySpline> propriedade; o que é o que torna um quadro-chave spline diferente de outros tipos de quadros-chave.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Uma curva de Bézier cúbica é definida por um ponto inicial, um ponto final e dois pontos de controle. O <xref:System.Windows.Media.Animation.KeySpline> propriedade de um quadro-chave spline define os dois pontos de controle de uma curva de Bézier que se estende de (0,0) a (1,1). O primeiro ponto de controle controla o fator de curva da primeira metade da curva de Bézier e o segundo ponto de controle controla o fator de curva da segunda metade do segmento de Bézier. A curva resultante descreve a taxa de alteração desse quadro-chave spline. Quanto mais íngreme for a curva, mais rápido o quadro-chave mudará seus valores. Conforme a curva fica mais plana, o quadro-chave muda seus valores mais lentamente.  
  
 Você pode usar <xref:System.Windows.Media.Animation.KeySpline> para simular trajetórias físicas como água caindo ou bolas saltitante ou aplicar outros "facilitar em" e "afastamento" efeitos a animações de movimento. Para efeitos de interação do usuário como esmaecimento da tela de fundo ou reassociação do botão de controle, você poderá aplicar a interpolação spline para acelerar ou diminuir a taxa de alteração de uma animação de uma maneira específica.  
  
 O exemplo a seguir especifica um <xref:System.Windows.Media.Animation.KeySpline> de 0,1, 1,0, que cria a curva de Bézier a seguir.  
  
 ![Uma curva de Bézier](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Um spline-chave com pontos de controle (0,0, 1,0) e (1,0, 0,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Esse quadro-chave é animado rapidamente quando é iniciado, desacelera e, em seguida, acelera novamente antes de ser encerrado.  
  
 O exemplo a seguir especifica um <xref:System.Windows.Media.Animation.KeySpline> de 0.5,0.25 0.75,1.0, que cria a curva de Bézier a seguir.  
  
 ![Uma curva de Bézier](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Um spline-chave com pontos de controle (0,25, 0,5) e (0,75, 1,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Como a curvatura da curva de Bézier muda muito pouco, esse quadro-chave é animado a uma taxa quase constante; ele desacelera um pouco quase no final.  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> para animar a posição do retângulo. Porque o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> usa <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> objetos, a transição entre cada valor de quadro-chave usa a interpolação spline.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 A interpolação spline pode ser difícil de entender; pode ser útil testar diferentes configurações. A [Amostra de animação de spline-chave](https://go.microsoft.com/fwlink/?LinkID=160011) permite alterar os valores do spline-chave e ver o resultado na animação.  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>Combinando métodos de interpolação  
 É possível usar quadros-chave com diferentes tipos de interpolação em uma única animação de quadro-chave. Quando duas animações de quadro-chave com diferentes interpolações ocorrem uma após a outra, o método de interpolação do segundo quadro-chave é usado para criar a transição do primeiro valor para o segundo.  
  
 No exemplo a seguir, um <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> é criado que usa a interpolação linear, spline e discreta.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>Mais informações sobre duração e tempos-chave  
 Assim como outras animações, animações de quadro-chave têm uma <xref:System.Windows.Duration> propriedade. Além de especificar a animação <xref:System.Windows.Duration>, você precisa especificar qual parte da duração é fornecida para cada quadro-chave. Faça isso descrevendo um <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> para cada um dos quadros-chave da animação. Cada quadro chave <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> especifica esse quadro chave termina.  
  
 O <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriedade não especifica quanto tempo o tempo-chave é reproduzido. O tempo durante o qual um quadro-chave é reproduzido é determinado pelo tempo em que o quadro-chave é encerrado, pelo tempo em que o quadro-chave anterior foi encerrado e pela duração da animação. Tempos-chave podem ser especificados como um valor de tempo, uma porcentagem ou como os valores especiais <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 A lista a seguir descreve as diferentes maneiras de especificar os tempos-chave.  
  
### <a name="timespan-values"></a>Valores TimeSpan  
 Você pode usar <xref:System.TimeSpan> valores para especificar um <xref:System.Windows.Media.Animation.KeyTime>. O valor deve ser maior ou igual a 0 e menor ou igual à duração da animação. O exemplo a seguir mostra uma animação com uma duração de 10 segundos e quatro quadros-chave cujos tempos-chave são especificados como valores temporais.  
  
-   O primeiro quadro-chave é animado do valor base para 100 durante os primeiros 3 segundos, sendo encerrado no tempo = 0:0:03.  
  
-   O segundo quadro-chave é animado de 100 a 200. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 3 segundos) e é reproduzido por 5 segundos, sendo encerrado no tempo = 0:0:8.  
  
-   O terceiro quadro-chave é animado de 200 a 500. Ele é iniciado após o término do segundo quadro-chave (no tempo = 8 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:9.  
  
-   O quarto quadro-chave é animado de 500 a 600. Ele é iniciado após o término do terceiro quadro-chave (no tempo = 9 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Valores percentuais  
 Um valor percentual Especifica que o quadro chave termina em alguma porcentagem da animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você especifica o percentual como um número seguido pelo símbolo `%`. No código, você deve usar o <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> método e passá-lo um <xref:System.Double> indicando a porcentagem. O valor deve ser maior ou igual a 0 e menor ou igual a 100%. O exemplo a seguir mostra uma animação com uma duração de 10 segundos e quatro quadros-chave cujos tempos-chave são especificados como percentuais.  
  
-   O primeiro quadro-chave é animado do valor base para 100 durante os primeiros 3 segundos, sendo encerrado no tempo = 0:0:3.  
  
-   O segundo quadro-chave é animado de 100 a 200. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 3 segundos) e é reproduzido por 5 segundos, sendo encerrado no tempo = 0:0:8 (0,8 * 10 = 8).  
  
-   O terceiro quadro-chave é animado de 200 a 500. Ele é iniciado após o término do segundo quadro-chave (no tempo = 8 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:9 (0,9 * 10 = 9).  
  
-   O quarto quadro-chave é animado de 500 a 600. Ele é iniciado após o término do terceiro quadro-chave (no tempo = 9 segundos) e é reproduzido por 1 segundo, sendo encerrado no tempo = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Valor especial, uniforme  
 Use <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> de tempo quando desejar que cada quadro-chave Use a mesma quantidade de tempo.  
  
 Um <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> tempo-chave divide o tempo disponível igualmente pelo número de quadros-chave para determinar a hora de término de cada quadro chave. O exemplo a seguir mostra uma animação com uma duração de 10 segundos e quatro quadros-chave cujos momentos chave é especificados como <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
-   O primeiro quadro-chave é animado do valor base para 100 durante os primeiros 2,5 segundos, sendo encerrado no tempo = 0:0:2.5.  
  
-   O segundo quadro-chave é animado de 100 a 200. Ele é iniciado após o término do primeiro quadro-chave (no tempo = 2,5 segundos) e é reproduzido por aproximadamente 2,5 segundos, sendo encerrado no tempo = 0:0:5.  
  
-   O terceiro quadro-chave é animado de 200 a 500. Ele é iniciado após o término do segundo quadro-chave (no tempo = 5 segundos) e é reproduzido por 2,5 segundos, sendo encerrado no tempo = 0:0:7.5.  
  
-   O quarto quadro-chave é animado de 500 a 600. Ele é iniciado após o término do segundo quadro-chave (no tempo = 7,5 segundos) e é reproduzido por 2,5 segundos, sendo encerrado no tempo = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Valor especial, personalizado  
 Use <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> quando quiser animar a uma taxa constante de tempo.  
  
 Um <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> tempo-chave aloca o tempo disponível de acordo com a duração de cada um dos quadros chave para determinar a duração de cada quadro.  Isso fornecerá o comportamento em que a velocidade ou o ritmo da animação permanece constante.  O exemplo a seguir mostra uma animação com uma duração de 10 segundos e três quadros-chave cujos momentos chave são especificados como <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Observe que, se for de tempo-chave do último quadro chave <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, seu tempo-chave resolvido será definido para 100 por cento. Se o primeiro quadro-chave em uma animação com vários quadros for personalizado, seu tempo-chave resolvido será definido como 0. (Se a coleção de quadros-chave contiver apenas um único quadro-chave e ele for um quadro-chave personalizado, seu tempo-chave resolvido será definido como 100%.)  
  
 Diferentes quadros-chave em uma animação de quadro-chave único podem usar diferentes tipos de tempos-chave.  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>Combinando tempos-chave e quadros-chave fora de ordem  
 Você pode usar quadros-chave com diferentes <xref:System.Windows.Media.Animation.KeyTime> tipos na mesma animação de valor. E, embora seja recomendável adicionar quadros-chave na ordem em que eles devem ser reproduzidos, isso não é necessário. O sistema de animação e tempo pode resolver quadros-chave fora de ordem. Os quadros-chave com tempos-chave inválidos são ignorados.  
  
 A lista a seguir descreve o procedimento pelo qual os tempos-chave são resolvidos para os quadros-chave de uma animação de quadro-chave.  
  
1.  Resolver <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> valores.  
  
2.  Determine o *tempo total de interpolação* da animação, o tempo total necessário para que a animação de quadro-chave conclua uma interação progressiva.  
  
    1.  Se a animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A> não é <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>, o tempo total de interpolação é o valor da animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade.  
  
    2.  Caso contrário, o tempo total de interpolação será o maior <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> valor especificado entre seus quadros chave, se existir alguma.  
  
    3.  Caso contrário, o tempo total de interpolação será de 1 segundo.  
  
3.  Use o valor de tempo total de interpolação para resolver <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> valores.  
  
4.  Resolva o último quadro-chave, caso ele ainda não tenha sido resolvido nas etapas anteriores. Se o <xref:System.Windows.Media.Animation.KeyTime> do último quadro-chave é <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, seu tempo resolvido será igual ao tempo total de interpolação.  
  
     Se o <xref:System.Windows.Media.Animation.KeyTime> é o primeiro quadro-chave <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> e essa animação tiver mais de quadros de chave, resolva seu <xref:System.Windows.Media.Animation.KeyTime> valor como zero; se houver apenas um quadro chave e seu <xref:System.Windows.Media.Animation.KeyTime> valor é <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, é resolvido para o total tempo de interpolação, conforme descrito na etapa anterior.  
  
5.  Resolve os demais <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> valores: cada um recebe uma parte igual do tempo disponível.  Durante esse processo, não resolvido <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> valores são tratados temporariamente como <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> valores e obtenha um momento resolvido temporário.  
  
6.  Resolver o <xref:System.Windows.Media.Animation.KeyTime> valores de quadros-chave com momentos chave não especificados usando quadros chave declarados mais próximos deles que tenham resolvido <xref:System.Windows.Media.Animation.KeyTime> valores.  
  
7.  Resolve os demais <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> valores. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> Use o <xref:System.Windows.Media.Animation.KeyTime> valores de vizinhos quadros para determinar seus tempos resolvidos da chave.  O objetivo é garantir que a velocidade da animação é constante em relação ao tempo resolvido desse quadro-chave.  
  
8.  Classifique os quadros-chave na ordem de tempo resolvido (chave primária) e ordem de declaração (chave secundária), ou seja, use uma classificação estável com base no quadro-chave resolvido <xref:System.Windows.Media.Animation.KeyTime> valores.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Exemplo de animação de spline-chave](https://go.microsoft.com/fwlink/?LinkID=160011)
- [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012)
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)
- [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md)
