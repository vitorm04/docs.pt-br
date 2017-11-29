---
title: Como animar cor usando quadros-chave
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
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d117d57e5cc761aa2f31fd6531bff8d96ea30dc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Como animar cor usando quadros-chave
Este exemplo mostra como animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usando quadros chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriedade de um <xref:System.Windows.Media.SolidColorBrush>. Essa animação usa três quadros-chave da seguinte maneira:  
  
1.  Durante os primeiros dois segundos, usa uma instância do <xref:System.Windows.Media.Animation.LinearColorKeyFrame> classe para alterar a cor gradualmente de verde para vermelho. Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearColorKeyFrame> criam uma transição linear suave entre valores.  
  
2.  Durante o final do próximo meio segundo, usa uma instância do <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> classe para alterar rapidamente a cor de vermelho para amarelo. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> criam alterações repentinas entre valores, ou seja, a alteração de cor nesta parte da animação ocorre rapidamente e não é sutil.  
  
3.  Durante os últimos dois segundos, usa uma instância do <xref:System.Windows.Media.Animation.SplineColorKeyFrame> classe para alterar a cor novamente – desta vez de amarelo para verde. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineColorKeyFrame> criar uma transição de variável entre valores de acordo com os valores de <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> propriedade. Neste exemplo, a alteração na cor começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
