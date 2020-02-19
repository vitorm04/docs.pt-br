---
title: Visão geral de animações de-para-por
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 661c035f55ba1fb550726d75921cd01a72b2eecc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448994"
---
# <a name="fromtoby-animations-overview"></a>Visão geral de animações de/para/por
Este tópico descreve como usar animações de/para/por para animar propriedades de dependência. Uma animação de/para/por cria uma transição entre dois valores.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Para entender este tópico, você deve estar familiarizado com os recursos de animações de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter uma introdução aos recursos de animação, consulte a [visão geral da animação](animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>O que é uma animação de/para/por?  
 Uma animação de/para/por é um tipo de <xref:System.Windows.Media.Animation.AnimationTimeline> que cria uma transição entre um valor inicial e um valor final. A quantidade de tempo que a transição leva para ser concluída é determinada pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A> dessa animação.  
  
 Você pode aplicar uma animação de/para/por a uma propriedade usando um <xref:System.Windows.Media.Animation.Storyboard> em marcação e código, ou usando o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> no código. Você também pode usar uma animação de/para/por para criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-lo a uma ou mais propriedades. Para obter mais informações sobre os diferentes métodos para aplicação de animações, consulte a [Visão geral das técnicas de animação de propriedades](property-animation-techniques-overview.md).  
  
 Animações de/para/por podem ter não mais do que dois valores de destino. Se você precisar de uma animação que tem mais de dois valores de destino, use uma animação de quadro-chave. As animações de quadro chave são descritas na [visão geral das animações de quadro chave](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Tipos de animação de/para/por  
 Como as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade que usa um <xref:System.Double>, como a propriedade <xref:System.Windows.FrameworkElement.Width%2A> de um elemento, use uma animação que produza valores de <xref:System.Double>. Para animar uma propriedade que usa um <xref:System.Windows.Point>, use uma animação que produz <xref:System.Windows.Point> valores, e assim por diante.  
  
 As classes de animação de/para/por pertencem ao namespace <xref:System.Windows.Media.Animation> e usam a seguinte convenção de nomenclatura:  
  
 *tipo de\<>* `Animation`  
  
 Em que *\<Type>* é o tipo de valor animado pela classe.  
  
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
 Uma animação de/para/por cria uma transição entre dois valores de destino. É comum especificar um valor inicial (defina-o usando a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>) e um valor final (defina-o usando a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>). No entanto, você também pode especificar apenas um valor inicial, um valor de destino ou um valor de deslocamento. Nesses casos, a animação obtém o valor de destino ausente da propriedade que está sendo animada. A lista a seguir descreve as diferentes maneiras de especificar os valores de destino de uma animação.  
  
- **Valor inicial**  
  
     Use a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> quando desejar especificar explicitamente o valor inicial de uma animação. Você pode usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> por si só ou com a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ou <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. Se você especificar apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, a animação passará desse valor para o valor base da propriedade animada.  
  
- **Valor final**  
  
     Para especificar um valor final de uma animação, use sua propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>. Se você usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> por si só, a animação obterá seu valor inicial da propriedade que está sendo animada ou da saída de outra animação que é aplicada à mesma propriedade. Você pode usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> junto com a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> para especificar explicitamente valores iniciais e finais para a animação.  
  
- **Valor de deslocamento**  
  
     A propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> permite que você especifique um deslocamento em vez de um valor de início ou término explícito para a animação. A propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de uma animação especifica por quanto a animação altera um valor ao longo de sua duração. Você pode usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> por si só ou com a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. Se você especificar apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, a animação adicionará o valor de deslocamento ao valor base da propriedade ou à saída de outra animação.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Usando valores de/para/por  
 As seções a seguir descrevem como usar as propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> juntas ou separadamente.  
  
 Os exemplos nesta seção usam um <xref:System.Windows.Media.Animation.DoubleAnimation>, que é um tipo de animação de/para/por, para animar a propriedade <xref:System.Windows.FrameworkElement.Width%2A> de um <xref:System.Windows.Shapes.Rectangle> que tem 10 pixels independentes de dispositivo de alta e 100 pixels independentes de largura de um dispositivo.  
  
 Embora cada exemplo use uma <xref:System.Windows.Media.Animation.DoubleAnimation>, as propriedades from, to e by de todas as animações de/para/por se comportam de forma idêntica. Embora cada um desses exemplos use uma <xref:System.Windows.Media.Animation.Storyboard>, você pode usar de/para/por animações de outras maneiras. Para obter mais informações, consulte [visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>De/Para  
 Quando você define os valores de <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> juntos, a animação progride do valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, para o valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 O exemplo a seguir define a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation> como 50 e sua propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> como 300. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> da <xref:System.Windows.Shapes.Rectangle> é animado de 50 para 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Para  
 Quando você define apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, a animação progride do valor base da propriedade animada ou da saída de uma animação de composição que foi aplicada anteriormente à mesma propriedade, ao valor que é especificado pela propriedade de <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 ("Animação de composição" refere-se a uma animação <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> aplicada anteriormente à mesma propriedade que ainda está em vigor quando a animação atual foi aplicada usando o comportamento de entrega do <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>.)  
  
 O exemplo a seguir define apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation> como 300. Como nenhum valor inicial foi especificado, o <xref:System.Windows.Media.Animation.DoubleAnimation> usa o valor base (100) da propriedade <xref:System.Windows.FrameworkElement.Width%2A> como seu valor inicial. O <xref:System.Windows.FrameworkElement.Width%2A> da <xref:System.Windows.Shapes.Rectangle> é animado de 100 para o valor de destino da animação de 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Por  
 Quando você define apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de uma animação, a animação progride do valor base da propriedade que está sendo animada, ou da saída de uma animação de composição para a soma desse valor e o valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 O exemplo a seguir define apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation> como 300. Como o exemplo não especifica um valor inicial, o <xref:System.Windows.Media.Animation.DoubleAnimation> usa o valor base da propriedade <xref:System.Windows.FrameworkElement.Width%2A>, 100, como seu valor inicial. O valor final é determinado pela adição do valor <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> da animação, 300, ao seu valor inicial, 100:400. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> da <xref:System.Windows.Shapes.Rectangle> é animado de 100 para 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>De/por  
 Quando você define as propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de uma animação, a animação progride a partir do valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, para o valor especificado pela soma das propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 O exemplo a seguir define a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation> como 50 e sua propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> como 300. O valor final é determinado pela adição do valor <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> da animação, 300, ao seu valor inicial, 50:350. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> da <xref:System.Windows.Shapes.Rectangle> é animado de 50 para 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>De  
 Quando você especifica apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> valor de uma animação, a animação progride do valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, para o valor base da propriedade que está sendo animada ou para a saída de uma animação de composição.  
  
 O exemplo a seguir define apenas a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation> como 50. Como nenhum valor final foi especificado, o <xref:System.Windows.Media.Animation.DoubleAnimation> usa o valor base da propriedade <xref:System.Windows.FrameworkElement.Width%2A>, 100, como seu valor final. O <xref:System.Windows.FrameworkElement.Width%2A> da <xref:System.Windows.Shapes.Rectangle> é animado de 50 para o valor base da propriedade <xref:System.Windows.FrameworkElement.Width%2A>, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Para/por  
 Se você definir as propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de uma animação, a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> será ignorada.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Outros tipos de animação  
 As animações de/para/por não são o único tipo de animações que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece: ela também fornece animações de quadro-chave e animações de caminho.  
  
- Uma animação de quadro-chave se anima com qualquer número de valores de destino, descritos usando quadros-chave. Para obter mais informações, consulte [visão geral das animações de quadro chave](key-frame-animations-overview.md).  
  
- Uma animação de caminho gera valores de saída de um <xref:System.Windows.Media.PathGeometry>. Para obter mais informações, consulte [visão geral de animações de caminho](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também permite que você crie seus próprios tipos de animação personalizada. Para obter mais informações, consulte [visão geral das animações personalizadas](custom-animations-overview.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Visão geral de animações de caminho](path-animations-overview.md)
- [Visão geral de animações personalizadas](custom-animations-overview.md)
- [Amostra de valores de destino de animação De, Para e Por](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
