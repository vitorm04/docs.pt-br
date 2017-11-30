---
title: "Como animar alterações de tamanho usando quadros-chave"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9577f9f08fa1d19aa214bda5a1aef997c2cfa2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="57f40-102">Como animar alterações de tamanho usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="57f40-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="57f40-103">Esse exemplo demonstra como animar alterações de tamanho usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="57f40-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57f40-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57f40-104">Example</span></span>  
 <span data-ttu-id="57f40-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.ArcSegment.Size%2A> propriedade de um <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="57f40-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="57f40-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="57f40-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="57f40-107">Durante a primeira metade de segundo da animação, usa uma instância do <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> classe gradualmente aumentar o tamanho do arco. Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> criam uma transição linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="57f40-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="57f40-108">No final do próximo meio segundo, usa uma instância do <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> classe repentinamente aumentar o tamanho do arco. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> criar saltos repentinos entre valores, ou seja, as alterações de tamanho ocorrem repentinamente e não são sutis.</span><span class="sxs-lookup"><span data-stu-id="57f40-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="57f40-109">Sobre os últimos dois segundos, usa uma instância do <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> classe para aumentar o tamanho do arco. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> criar uma transição de variável entre valores de acordo com os valores de <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="57f40-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="57f40-110">Neste exemplo, o tamanho do arco aumenta lentamente no início e aumenta exponencialmente até o final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="57f40-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="57f40-111">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="57f40-111">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f40-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57f40-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [<span data-ttu-id="57f40-113">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="57f40-113">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="57f40-114">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="57f40-114">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
