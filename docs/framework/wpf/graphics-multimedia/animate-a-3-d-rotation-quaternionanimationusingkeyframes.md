---
title: "Como animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89719cbcb72c5c24654962e9eb17a540224fd588
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="12813-102">Como animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="12813-102">How to: Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="12813-103">No exemplo a seguir, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> é usado para fazer com que um objeto 3D girar.</span><span class="sxs-lookup"><span data-stu-id="12813-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="12813-104">Essa animação usa quadros-chave a seguir:</span><span class="sxs-lookup"><span data-stu-id="12813-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="12813-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>é usado para criar uma interpolação linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="12813-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="12813-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>é usado para criar "saltos" repentinos entre valores (sem interpolação).</span><span class="sxs-lookup"><span data-stu-id="12813-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="12813-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>é usado para criar uma transição de variável entre valores dependendo do <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="12813-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="12813-108">No exemplo a seguir, essa parte da animação começa lentamente mas até o fim do segmento de tempo, acelera exponencialmente.</span><span class="sxs-lookup"><span data-stu-id="12813-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12813-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12813-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="12813-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12813-110">See Also</span></span>  
 [<span data-ttu-id="12813-111">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="12813-111">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="12813-112">Animar uma rotação 3D usando Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="12813-112">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="12813-113">Animar uma rotação 3D usando Quaternions</span><span class="sxs-lookup"><span data-stu-id="12813-113">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="12813-114">Animar uma rotação 3D usando quadros principais (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="12813-114">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="12813-115">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="12813-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="12813-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="12813-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
