---
title: 'Como: Animar uma rotação 3D usando quadros-chave'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 90e982838cb5d5b4488185c041e946c15d1e61e8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369130"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="37b0f-102">Como: Animar uma rotação 3D usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="37b0f-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="37b0f-103">No exemplo a seguir, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> é usado para fazer com que um objeto 3D rotacionar enquanto seu eixo de rotação anima, resultando em uma "tremida".</span><span class="sxs-lookup"><span data-stu-id="37b0f-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="37b0f-104">Essa animação usa quadros-chave a seguir:</span><span class="sxs-lookup"><span data-stu-id="37b0f-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="37b0f-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> é usado para criar uma interpolação linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="37b0f-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="37b0f-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> é usado para criar "saltos" repentinos entre valores (sem interpolação).</span><span class="sxs-lookup"><span data-stu-id="37b0f-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="37b0f-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> é usado para criar uma transição variável entre valores de acordo o <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="37b0f-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="37b0f-108">No exemplo a seguir, essa parte da animação começa lentamente, mas na direção do final do segmento de tempo, acelera exponencialmente.</span><span class="sxs-lookup"><span data-stu-id="37b0f-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37b0f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37b0f-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="37b0f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37b0f-110">See also</span></span>
- [<span data-ttu-id="37b0f-111">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="37b0f-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="37b0f-112">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="37b0f-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="37b0f-113">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="37b0f-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="37b0f-114">Animar uma rotação 3D usando Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="37b0f-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="37b0f-115">Animar uma rotação 3D usando Quaternions</span><span class="sxs-lookup"><span data-stu-id="37b0f-115">Animate a 3-D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="37b0f-116">Animar uma rotação 3D usando quadros principais (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="37b0f-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
