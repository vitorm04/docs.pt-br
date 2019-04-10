---
title: 'Como: Animar uma rotação 3D usando quadros principais (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 87176df26405a69cb2c3d63620def0575b750b52
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338014"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="bbf41-102">Como: Animar uma rotação 3D usando quadros principais (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="bbf41-102">How to: Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="bbf41-103">No exemplo a seguir, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> é usado para fazer com que um objeto 3D girar.</span><span class="sxs-lookup"><span data-stu-id="bbf41-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="bbf41-104">Essa animação usa quadros-chave a seguir:</span><span class="sxs-lookup"><span data-stu-id="bbf41-104">This animation uses the following key frames:</span></span>  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> <span data-ttu-id="bbf41-105">é usado para criar uma interpolação linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="bbf41-105">is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> <span data-ttu-id="bbf41-106">é usado para criar "saltos" repentinos entre valores (sem interpolação).</span><span class="sxs-lookup"><span data-stu-id="bbf41-106">is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> <span data-ttu-id="bbf41-107">é usado para criar uma transição variável entre valores de acordo o <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bbf41-107">is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="bbf41-108">No exemplo a seguir, essa parte da animação começa lentamente, mas na direção do final do segmento de tempo, acelera exponencialmente.</span><span class="sxs-lookup"><span data-stu-id="bbf41-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf41-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbf41-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bbf41-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbf41-110">See also</span></span>

- [<span data-ttu-id="bbf41-111">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="bbf41-111">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="bbf41-112">Animar uma rotação 3D usando Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="bbf41-112">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="bbf41-113">Animar uma rotação 3D usando quaternions</span><span class="sxs-lookup"><span data-stu-id="bbf41-113">Animate a 3-D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="bbf41-114">Animar uma rotação 3D usando quadros principais (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="bbf41-114">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="bbf41-115">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="bbf41-115">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="bbf41-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="bbf41-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
