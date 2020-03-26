---
title: Como animar a posição e a direção da câmera usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112161"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="c5765-102">Como animar a posição e a direção da câmera usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="c5765-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="c5765-103">No exemplo a <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> seguir, é usado para <xref:System.Windows.Media.Media3D.PerspectiveCamera> animar a posição de a em uma cena 3D.</span><span class="sxs-lookup"><span data-stu-id="c5765-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="c5765-104">Além disso, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> é usado para animar a direção que a câmera está apontando na cena 3D.</span><span class="sxs-lookup"><span data-stu-id="c5765-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="c5765-105">Ambas as animações usam vários quadros-chave que criam uma série de efeitos de animação:</span><span class="sxs-lookup"><span data-stu-id="c5765-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1. <span data-ttu-id="c5765-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>e <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> são usados para criar uma interpolação suave e linear entre valores.</span><span class="sxs-lookup"><span data-stu-id="c5765-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="c5765-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>e <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> são usados para criar "saltos" repentinos entre valores (sem interpolação).</span><span class="sxs-lookup"><span data-stu-id="c5765-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="c5765-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>e <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> são usados para criar uma <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> transição variável entre valores dependendo da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c5765-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="c5765-109">No exemplo abaixo, a animação começa lenta, mas no final do segmento de tempo, acelera exponencialmente.</span><span class="sxs-lookup"><span data-stu-id="c5765-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5765-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5765-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c5765-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5765-111">See also</span></span>

- [<span data-ttu-id="c5765-112">Animar posição e direção da câmera em uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="c5765-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="c5765-113">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="c5765-113">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
