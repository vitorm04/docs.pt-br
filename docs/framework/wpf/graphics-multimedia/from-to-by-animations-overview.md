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
ms.openlocfilehash: 40a37542d6151d05910bc033657d85c6a9f5483b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362754"
---
# <a name="fromtoby-animations-overview"></a>Visão geral de animações de/para/por
Este tópico descreve como usar animações de/para/por para animar propriedades de dependência. Uma animação de/para/por cria uma transição entre dois valores.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] recursos de animações. Para obter uma introdução a recursos de animação, consulte o [visão geral da animação](animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>O que é uma animação de/para/por?  
 Um de/para/por animação é um tipo de <xref:System.Windows.Media.Animation.AnimationTimeline> que cria uma transição entre um valor inicial e um valor final. A quantidade de tempo que a transição leva para concluir é determinada pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A> daquela animação.  
  
 Você pode aplicar um de/para/por animação a uma propriedade usando um <xref:System.Windows.Media.Animation.Storyboard> na marcação e código, ou usando o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método no código. Você também pode usar uma animação de From/To/By para criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-lo a uma ou mais propriedades. Para obter mais informações sobre os diferentes métodos para aplicação de animações, consulte a [Visão geral das técnicas de animação de propriedades](property-animation-techniques-overview.md).  
  
 Animações de/para/por podem ter não mais do que dois valores de destino. Se você precisar de uma animação que tem mais de dois valores de destino, use uma animação de quadro-chave. Animações de quadro-chave são descritas na [visão geral de animações de quadro-chave](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Tipos de animação de/para/por  
 Como as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade que utiliza um <xref:System.Double>, como o <xref:System.Windows.FrameworkElement.Width%2A> propriedade de um elemento, use uma animação que produz <xref:System.Double> valores. Para animar uma propriedade que utiliza um <xref:System.Windows.Point>, use uma animação que produz <xref:System.Windows.Point> valores e assim por diante.  
  
 Classes de animação de/para/por pertencem ao <xref:System.Windows.Media.Animation> namespace e use a seguinte convenção de nomenclatura:  
  
 *\<Type>* `Animation`  
  
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
 Uma animação de/para/por cria uma transição entre dois valores de destino. É comum especificar um valor inicial (configurá-lo usando o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade) e um valor final (configurá-lo usando o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade). No entanto, você também pode especificar apenas um valor inicial, um valor de destino ou um valor de deslocamento. Nesses casos, a animação obtém o valor de destino ausente da propriedade que está sendo animada. A lista a seguir descreve as diferentes maneiras de especificar os valores de destino de uma animação.  
  
-   **Valor inicial**  
  
     Use o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> quando você deseja especificar explicitamente o valor inicial de uma animação de propriedade. Você pode usar o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade por si só, ou com o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ou <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade. Se você especificar apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade, a animação faz a transição desse valor ao valor base da propriedade animada.  
  
-   **Valor final**  
  
     Para especificar um valor final de uma animação, use seu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade. Se você usar o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade por si só, a animação obtém o valor inicial da propriedade que está sendo animada ou da saída de outra animação que é aplicada à mesma propriedade. Você pode usar o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade junto com o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para especificar explicitamente valores para a animação inicial e final.  
  
-   **Valor de deslocamento**  
  
     O <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade permite que você especifique um deslocamento, em vez de um explícito valor inicial ou final da animação. O <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade de uma animação especifica por quanto a animação altera um valor sobre sua duração. Você pode usar o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade sozinho ou com o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade. Se você especificar apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade, a animação adiciona o valor de deslocamento ao valor base da propriedade ou a saída de outra animação.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Usando valores de/para/por  
 As seções a seguir descrevem como usar o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades juntas ou separadamente.  
  
 Os exemplos desta seção cada um usa um <xref:System.Windows.Media.Animation.DoubleAnimation>, que é um tipo de animação de/para/por, para animar a <xref:System.Windows.FrameworkElement.Width%2A> propriedade de um <xref:System.Windows.Shapes.Rectangle> que é 10 pixels independentes de dispositivo alta e 100 pixels independentes de dispositivo amplas.  
  
 Embora cada exemplo utiliza um <xref:System.Windows.Media.Animation.DoubleAnimation>, o From, To e By propriedades de todos os de/para/por animações têm comportamento idêntico. Embora cada um desses exemplos usa um <xref:System.Windows.Media.Animation.Storyboard>, você pode usar animações de/para/por de outras maneiras. Para obter mais informações, consulte [visão geral das técnicas de animação de propriedade](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>De/para  
 Quando você define o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> valores juntos, a animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade, como o valor que é especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.  
  
 O exemplo a seguir define o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade do <xref:System.Windows.Media.Animation.DoubleAnimation> como 50 e sua <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade para 300. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> do <xref:System.Windows.Shapes.Rectangle> é animado de 50 a 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Para  
 Quando você define apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade, a animação progride do valor base da propriedade animada ou da saída de uma animação composta que foi anteriormente aplicada à mesma propriedade, como o valor que é especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.  
  
 ("Animação de composição" refere-se a um <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> animação que anteriormente aplicada à mesma propriedade que ainda está em vigor quando a animação atual foi aplicada usando o <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> comportamento de entrega.)  
  
 O exemplo a seguir define apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade do <xref:System.Windows.Media.Animation.DoubleAnimation> para 300. Como nenhum valor inicial foi especificado, o <xref:System.Windows.Media.Animation.DoubleAnimation> usa o valor base (100) do <xref:System.Windows.FrameworkElement.Width%2A> propriedade como seu valor inicial. O <xref:System.Windows.FrameworkElement.Width%2A> do <xref:System.Windows.Shapes.Rectangle> é animado de 100 para valor de destino da animação de 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Por  
 Quando você define apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade de uma animação, a animação progride do valor base da propriedade que está sendo animada ou da saída de uma animação composta para a soma desse valor e o valor especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade.  
  
 O exemplo a seguir define apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade do <xref:System.Windows.Media.Animation.DoubleAnimation> para 300. Como o exemplo não especifica um valor inicial, o <xref:System.Windows.Media.Animation.DoubleAnimation> usa o valor de base a <xref:System.Windows.FrameworkElement.Width%2A> propriedade, 100, como seu valor inicial. O valor final é determinado adicionando o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> valor da animação, 300, para seu valor inicial, 100: 400. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> do <xref:System.Windows.Shapes.Rectangle> é animado de 100 a 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>De/por  
 Quando você define o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades de uma animação, a animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade, como o valor que é especificado pela soma dos <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades.  
  
 O exemplo a seguir define o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade do <xref:System.Windows.Media.Animation.DoubleAnimation> como 50 e sua <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade para 300. O valor final é determinado adicionando o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> valor da animação, 300, para seu valor inicial, 50: 350. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> do <xref:System.Windows.Shapes.Rectangle> é animado de 50 a 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>De  
 Quando você especifica apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> valor de uma animação, a animação progride do valor especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade, como o valor base da propriedade que está sendo animada ou a saída de uma animação composta.  
  
 O exemplo a seguir define apenas o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade do <xref:System.Windows.Media.Animation.DoubleAnimation> como 50. Como nenhum valor final foi especificado, o <xref:System.Windows.Media.Animation.DoubleAnimation> usa o valor de base a <xref:System.Windows.FrameworkElement.Width%2A> propriedade, 100, como seu valor final. O <xref:System.Windows.FrameworkElement.Width%2A> do <xref:System.Windows.Shapes.Rectangle> é animado de 50 para valor de base a <xref:System.Windows.FrameworkElement.Width%2A> propriedade, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Para/por  
 Se você definir ambos os <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> e o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades de uma animação, o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade será ignorada.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Outros tipos de animação  
 Animações de/para/por não são o único tipo de animação que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece: também fornece animações de quadro-chave e animações de caminho.  
  
-   Uma animação de quadro-chave se anima com qualquer número de valores de destino, descritos usando quadros-chave. Para obter mais informações, consulte o [visão geral de animações de quadro-chave](key-frame-animations-overview.md).  
  
-   Uma animação de caminho gera valores de saída para um <xref:System.Windows.Media.PathGeometry>. Para obter mais informações, consulte o [visão geral de animações de caminho](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também permite que você crie seus próprios tipos de animação personalizada. Para obter mais informações, consulte o [visão geral de animações personalizadas](custom-animations-overview.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Visão geral de animações de caminho](path-animations-overview.md)
- [Visão geral de animações personalizadas](custom-animations-overview.md)
- [Amostra de valores de destino de animação De, Para e Por](https://go.microsoft.com/fwlink/?LinkID=159988)
