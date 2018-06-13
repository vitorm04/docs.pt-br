---
title: Como definir uma propriedade depois de animá-la com um storyboard
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: b8e9c08075b13f8d6f701d5ac6ae4f8ea8949184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562252"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Como definir uma propriedade depois de animá-la com um storyboard
Em alguns casos, pode parecer que não é possível alterar o valor de uma propriedade depois dela ter sido animada.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, uma <xref:System.Windows.Media.Animation.Storyboard> é usado para animar a cor de um <xref:System.Windows.Media.SolidColorBrush>. O storyboard é disparado ao clicar no botão. O <xref:System.Windows.Media.Animation.Timeline.Completed> evento é tratado para que o programa seja notificado quando o <xref:System.Windows.Media.Animation.ColorAnimation> é concluída.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Exemplo  
 Após a <xref:System.Windows.Media.Animation.ColorAnimation> for concluída, o programa tenta alterar a cor do pincel para azul.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 O código anterior parece não fazer nada: o pincel permanece amarelo, que é o valor fornecido pelo <xref:System.Windows.Media.Animation.ColorAnimation> que o pincel de animação. O valor da propriedade subjacente (o valor de base) é efetivamente alterado para azul. No entanto, o valor efetivo atual, ou, permanece amarelo porque o <xref:System.Windows.Media.Animation.ColorAnimation> ainda está substituindo o valor base. Se desejar que o valor de base se torne o valor efetivo novamente, você deverá impedir que a animação influencie a propriedade. Há três maneiras de fazer isso com animações do storyboard:  
  
-   Definir a animação <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   Remova todo o storyboard.  
  
-   Remova a animação da propriedade individual.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Definir a propriedade FillBehavior da animação como Parar  
 Definindo <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> para <xref:System.Windows.Media.Animation.FillBehavior.Stop>, você indica que a animação deve parar de afetar sua propriedade de destino após atingir o final do seu período ativo.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Remover todo o storyboard  
 Usando um <xref:System.Windows.Media.Animation.RemoveStoryboard> gatilho ou a <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> método, você indica que as animações de storyboard para parar de afetar suas propriedades de destino. A diferença entre essa abordagem e o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> é de propriedade que você pode remover o storyboard a qualquer momento, enquanto o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade só tem efeito quando a animação atinge o final do seu período ativo.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Remover uma animação de uma propriedade individual  
 Outra técnica para interromper uma animação de afetar uma propriedade é usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> método do objeto que está sendo animado. Especifique a propriedade sendo animada como o primeiro parâmetro e `null` como o segundo.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Essa técnica também funciona para animações que não são do storyboard.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
