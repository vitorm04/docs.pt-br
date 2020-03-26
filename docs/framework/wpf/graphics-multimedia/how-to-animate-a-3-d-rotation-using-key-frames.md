---
title: 'Como: Animar uma rotação 3D usando quadros-chave'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112304"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a><span data-ttu-id="d8452-102">Como: Animar uma rotação 3D usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="d8452-102">How to: Animate a 3D Rotation Using Key Frames</span></span>
<span data-ttu-id="d8452-103">No exemplo a <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> seguir, é usado para fazer um objeto 3D girar enquanto seu eixo de rotação anima resultando em uma "oscilação".</span><span class="sxs-lookup"><span data-stu-id="d8452-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="d8452-104">Esta animação usa os seguintes quadros-chave:</span><span class="sxs-lookup"><span data-stu-id="d8452-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="d8452-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>é usado para criar uma interpolação suave e linear entre valores.</span><span class="sxs-lookup"><span data-stu-id="d8452-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="d8452-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>é usado para criar "saltos" repentinos entre valores (sem interpolação).</span><span class="sxs-lookup"><span data-stu-id="d8452-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="d8452-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>é usado para criar uma transição <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variável entre valores dependendo da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8452-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="d8452-108">No exemplo abaixo, esta parte da animação começa lenta, mas no final do segmento de tempo, acelera exponencialmente.</span><span class="sxs-lookup"><span data-stu-id="d8452-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8452-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8452-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d8452-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="d8452-110">See also</span></span>

- [<span data-ttu-id="d8452-111">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="d8452-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="d8452-112">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="d8452-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="d8452-113">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="d8452-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="d8452-114">Animar uma rotação 3D usando rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="d8452-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="d8452-115">Animar uma rotação 3D usando quaternions</span><span class="sxs-lookup"><span data-stu-id="d8452-115">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="d8452-116">Animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="d8452-116">Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
