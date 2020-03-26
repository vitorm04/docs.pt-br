---
title: 'Como: Animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112291"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="76483-102">Como: Animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="76483-102">How to: Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="76483-103">No exemplo a <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> seguir, é usado para fazer um objeto 3D girar.</span><span class="sxs-lookup"><span data-stu-id="76483-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="76483-104">Esta animação usa os seguintes quadros-chave:</span><span class="sxs-lookup"><span data-stu-id="76483-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="76483-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>é usado para criar uma interpolação suave e linear entre valores.</span><span class="sxs-lookup"><span data-stu-id="76483-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="76483-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>é usado para criar "saltos" repentinos entre valores (sem interpolação).</span><span class="sxs-lookup"><span data-stu-id="76483-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="76483-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>é usado para criar uma transição <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variável entre valores dependendo da propriedade.</span><span class="sxs-lookup"><span data-stu-id="76483-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="76483-108">No exemplo abaixo, esta parte da animação começa lenta, mas no final do segmento de tempo, acelera exponencialmente.</span><span class="sxs-lookup"><span data-stu-id="76483-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76483-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76483-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="76483-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="76483-110">See also</span></span>

- [<span data-ttu-id="76483-111">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="76483-111">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="76483-112">Animar uma rotação 3D usando rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="76483-112">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="76483-113">Animar uma rotação 3D usando quaternions</span><span class="sxs-lookup"><span data-stu-id="76483-113">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="76483-114">Animar uma rotação 3D usando quadros-chave (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="76483-114">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="76483-115">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="76483-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="76483-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="76483-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
