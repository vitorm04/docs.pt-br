---
title: Visão geral das animações de a despor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 135f01823d374b30f8d4d41762d2267a254f98c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186456"
---
# <a name="fromtoby-animations-overview"></a>Visão geral de animações de/para/por
Este tópico descreve como usar animações de/para/por para animar propriedades de dependência. Uma animação de/para/por cria uma transição entre dois valores.  
  
<a name="prereq"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deve estar familiarizado com os recursos de animações. Para obter uma introdução aos recursos de animação, consulte a [visão geral da animação](animation-overview.md).  
  
<a name="whatisanimation"></a>
## <a name="what-is-a-fromtoby-animation"></a>O que é uma animação de/para/por?  
 A From/To/By animation é <xref:System.Windows.Media.Animation.AnimationTimeline> um tipo de que cria uma transição entre um valor inicial e um valor final. A quantidade de tempo que a transição <xref:System.Windows.Media.Animation.Timeline.Duration%2A> leva para ser concluída é determinada pela animação.  
  
 Você pode aplicar uma animação De/To/By <xref:System.Windows.Media.Animation.Storyboard> a uma propriedade usando uma <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> marcação e código em uma marcação ou usando o método em código. Você também pode usar uma animação De/Para/Por para criar uma <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-la a uma ou mais propriedades. Para obter mais informações sobre os diferentes métodos para aplicar animações, consulte a visão geral das [técnicas de animação de propriedade](property-animation-techniques-overview.md).  
  
 Animações de/para/por podem ter não mais do que dois valores de destino. Se você precisar de uma animação que tem mais de dois valores de destino, use uma animação de quadro-chave. As animações de quadro-chave são descritas na visão geral das [animações do quadro-chave](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>
## <a name="fromtoby-animation-types"></a>Tipos de animação de/para/por  
 Como as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade <xref:System.Double>que toma <xref:System.Windows.FrameworkElement.Width%2A> um , como a propriedade de <xref:System.Double> um elemento, use uma animação que produz valores. Para animar uma propriedade <xref:System.Windows.Point>que leva um , <xref:System.Windows.Point> use uma animação que produz valores, e assim por diante.  
  
 As classes de animação de/Para/Por/By pertencem ao <xref:System.Windows.Media.Animation> namespace e usam a seguinte convenção de nomeação:  
  
 * \<Digite>*`Animation`  
  
 Onde * \<o tipo>* é o tipo de valor que a classe anima.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece as classes de animação de/para/por a seguir.  
  
|Tipo de propriedade|Classe de animação De/Para/Por correspondente|  
|-------------------|------------------------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>
## <a name="target-values"></a>Valores de destino  
 Uma animação de/para/por cria uma transição entre dois valores de destino. É comum especificar um valor inicial <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> (configurá-lo usando a propriedade) <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> e um valor final (defina-o usando a propriedade). No entanto, você também pode especificar apenas um valor inicial, um valor de destino ou um valor de deslocamento. Nesses casos, a animação obtém o valor de destino ausente da propriedade que está sendo animada. A lista a seguir descreve as diferentes maneiras de especificar os valores de destino de uma animação.  
  
- **Valor inicial**  
  
     Use <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a propriedade quando quiser especificar explicitamente o valor inicial de uma animação. Você pode <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> usar a propriedade sozinho, ou com a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Se você especificar apenas a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade, a animação passa desse valor para o valor base da propriedade animada.  
  
- **Valor final**  
  
     Para especificar um valor final <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> de uma animação, use sua propriedade. Se você <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> usar a propriedade por si só, a animação obtém seu valor inicial a partir da propriedade que está sendo animada ou da saída de outra animação que é aplicada à mesma propriedade. Você pode <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> usar a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade juntamente com a propriedade para especificar explicitamente valores de início e final para a animação.  
  
- **Valor de deslocamento**  
  
     A <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade permite que você especifique um deslocamento em vez de um valor explícito de inicialização ou final para a animação. A <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade de uma animação especifica o quanto a animação altera um valor ao longo de sua duração. Você pode <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> sozinho ou com a propriedade. Se você especificar apenas a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade, a animação adicionará o valor de deslocamento ao valor base da propriedade ou à saída de outra animação.  
  
<a name="examples"></a>
## <a name="using-fromtoby-values"></a>Usando valores de/para/por  
 As seções a seguir <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>descrevem <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>como <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> usar as propriedades e propriedades em conjunto ou separadamente.  
  
 Os exemplos nesta seção <xref:System.Windows.Media.Animation.DoubleAnimation>usam um , que é um tipo de animação <xref:System.Windows.FrameworkElement.Width%2A> From/To/By, para animar a propriedade de um <xref:System.Windows.Shapes.Rectangle> que tem 10 pixels independentes de dispositivo e 100 pixels independentes de dispositivo de largura.  
  
 Embora cada exemplo <xref:System.Windows.Media.Animation.DoubleAnimation>use um , o From, To, e por propriedades de todas as animações From/To/By se comportam de forma idêntica. Embora cada um desses <xref:System.Windows.Media.Animation.Storyboard>exemplos use um , você pode usar de/para/por animações de outras maneiras. Para obter mais informações, consulte [Visão geral das técnicas de animação de propriedade](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>De/para  
 Quando você <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> define <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> os valores e valores juntos, a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> animação progride do valor especificado pela propriedade, para o valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> seguir <xref:System.Windows.Media.Animation.DoubleAnimation> define a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> do até 50 e sua propriedade para 300. Como resultado, <xref:System.Windows.FrameworkElement.Width%2A> o <xref:System.Windows.Shapes.Rectangle> do é animado de 50 a 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Para  
 Quando você define <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> apenas a propriedade, a animação progride do valor base da propriedade animada, ou da saída de uma animação de composição <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> que foi anteriormente aplicada à mesma propriedade, até o valor especificado pela propriedade.  
  
 ("Compor animação" refere-se a uma <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> animação que anteriormente aplicada à mesma propriedade que ainda <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> está em vigor quando a animação atual foi aplicada usando o comportamento de handoff.)  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> seguir define <xref:System.Windows.Media.Animation.DoubleAnimation> apenas a propriedade dos 300. Como nenhum valor inicial foi <xref:System.Windows.Media.Animation.DoubleAnimation> especificado, utiliza o valor <xref:System.Windows.FrameworkElement.Width%2A> base (100) da propriedade como seu valor inicial. O <xref:System.Windows.FrameworkElement.Width%2A> do <xref:System.Windows.Shapes.Rectangle> é animado de 100 para o valor-alvo da animação de 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Por  
 Quando você define <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> apenas a propriedade de uma animação, a animação progride do valor base da propriedade que está sendo animada, ou da saída <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de uma animação de composição para a soma desse valor e o valor especificado pela propriedade.  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> seguir define <xref:System.Windows.Media.Animation.DoubleAnimation> apenas a propriedade dos 300. Como o exemplo não especifica um <xref:System.Windows.Media.Animation.DoubleAnimation> valor inicial, <xref:System.Windows.FrameworkElement.Width%2A> utiliza o valor base da propriedade, 100, como seu valor inicial. O valor final é <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> determinado adicionando o valor da animação, 300, ao seu valor inicial, 100: 400. Como resultado, <xref:System.Windows.FrameworkElement.Width%2A> o <xref:System.Windows.Shapes.Rectangle> do é animado de 100 a 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>De/por  
 Quando você <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> define <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> as propriedades de uma animação, a animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade, para <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> o valor especificado pela soma das propriedades.  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> seguir <xref:System.Windows.Media.Animation.DoubleAnimation> define a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> do até 50 e sua propriedade para 300. O valor final é <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> determinado adicionando o valor da animação, 300, ao seu valor inicial, 50: 350. Como resultado, <xref:System.Windows.FrameworkElement.Width%2A> o <xref:System.Windows.Shapes.Rectangle> do é animado de 50 a 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>De  
 Quando você especifica <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> apenas o valor de uma animação, a animação <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> progride do valor especificado pela propriedade, para o valor base da propriedade que está sendo animada ou para a saída de uma animação de composição.  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> seguir define <xref:System.Windows.Media.Animation.DoubleAnimation> apenas a propriedade do a 50. Como não foi especificado <xref:System.Windows.Media.Animation.DoubleAnimation> o valor final, <xref:System.Windows.FrameworkElement.Width%2A> utiliza o valor base do imóvel, 100, como seu valor final. O <xref:System.Windows.FrameworkElement.Width%2A> do <xref:System.Windows.Shapes.Rectangle> é animado de 50 para <xref:System.Windows.FrameworkElement.Width%2A> o valor base da propriedade, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Para/por  
 Se você definir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> as <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades de uma <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animação, a propriedade será ignorada.  
  
<a name="otheranimationtypes"></a>
## <a name="other-animation-types"></a>Outros tipos de animação  
 As animações de/Para/By não são o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] único tipo de animação que fornece: ele também fornece animações de quadro-chave e animações de caminho.  
  
- Uma animação de quadro-chave se anima com qualquer número de valores de destino, descritos usando quadros-chave. Para obter mais informações, consulte a visão geral das [animações do quadro-chave](key-frame-animations-overview.md).  
  
- Uma animação de caminho <xref:System.Windows.Media.PathGeometry>gera valores de saída a partir de um . Para obter mais informações, consulte a visão geral das [animações de caminho](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também permite que você crie seus próprios tipos de animação personalizada. Para obter mais informações, consulte a visão geral das [animações personalizadas](custom-animations-overview.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Visão geral de animações de caminho](path-animations-overview.md)
- [Visão geral de animações personalizadas](custom-animations-overview.md)
- [Amostra de valores de destino de animação De, Para e Por](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
