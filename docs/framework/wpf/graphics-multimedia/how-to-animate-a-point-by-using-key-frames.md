---
title: Como animar um ponto usando quadros-chave
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f574f85a5840e8bbe2d6c026d57a4cc28bd8a797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Como animar um ponto usando quadros-chave
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe para animar uma <xref:System.Windows.Point>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir move uma elipse ao longo de um caminho triangular. O exemplo usa o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade de um <xref:System.Windows.Media.EllipseGeometry>. Essa animação usa três quadros-chave da seguinte maneira:  
  
1.  Durante a primeira metade de segundo, usa uma instância do <xref:System.Windows.Media.Animation.LinearPointKeyFrame> classe para mover a elipse ao longo de um caminho a uma taxa constante de sua posição inicial. Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearPointKeyFrame> criam uma interpolação linear suave entre valores.  
  
2.  Durante o final do próximo meio segundo, usa uma instância do <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> classe repentinamente mover a elipse ao longo do caminho para a próxima posição. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> criar saltos repentinos entre valores.  
  
3.  Durante os últimos dois segundos, usa uma instância do <xref:System.Windows.Media.Animation.SplinePointKeyFrame> classe para mover a elipse de volta para sua posição inicial. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplinePointKeyFrame> criar uma transição de variável entre valores de acordo com os valores de <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> propriedade. Neste exemplo, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Para manter a consistência com outros exemplos de animação, as versões de código deste exemplo usam um <xref:System.Windows.Media.Animation.Storyboard> objeto ao qual aplicar o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. No entanto, ao aplicar uma única animação no código, é mais simples usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método em vez de usar um <xref:System.Windows.Media.Animation.Storyboard>. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
