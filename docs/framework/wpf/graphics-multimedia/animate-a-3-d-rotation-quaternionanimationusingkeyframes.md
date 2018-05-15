---
title: Como animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 59514dcd617f73cc8c8e458dc13880b3521c0fb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="c4e2a-102">Como animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="c4e2a-102">How to: Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="c4e2a-103">No exemplo a seguir, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> é usado para fazer com que um objeto 3D girar.</span><span class="sxs-lookup"><span data-stu-id="c4e2a-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="c4e2a-104">Essa animação usa quadros-chave a seguir:</span><span class="sxs-lookup"><span data-stu-id="c4e2a-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="c4e2a-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> é usado para criar uma interpolação linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="c4e2a-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="c4e2a-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> é usado para criar "saltos" repentinos entre valores (sem interpolação).</span><span class="sxs-lookup"><span data-stu-id="c4e2a-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="c4e2a-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> é usado para criar uma transição de variável entre valores dependendo do <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c4e2a-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="c4e2a-108">No exemplo a seguir, essa parte da animação começa lentamente mas até o fim do segmento de tempo, acelera exponencialmente.</span><span class="sxs-lookup"><span data-stu-id="c4e2a-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4e2a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c4e2a-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c4e2a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4e2a-110">See Also</span></span>  
 [<span data-ttu-id="c4e2a-111">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="c4e2a-111">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="c4e2a-112">Animar uma rotação 3D usando Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="c4e2a-112">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="c4e2a-113">Animar uma rotação 3D usando Quaternions</span><span class="sxs-lookup"><span data-stu-id="c4e2a-113">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="c4e2a-114">Animar uma rotação 3D usando quadros principais (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="c4e2a-114">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="c4e2a-115">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="c4e2a-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="c4e2a-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="c4e2a-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
