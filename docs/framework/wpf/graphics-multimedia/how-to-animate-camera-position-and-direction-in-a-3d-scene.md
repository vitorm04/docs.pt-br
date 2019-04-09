---
title: 'Como: Animar posição e direção da câmera em uma cena 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: b64263a495ffe845a76317aad8f5b4a14e11b31e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145997"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="9065a-102">Como: Animar posição e direção da câmera em uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="9065a-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="9065a-103">O exemplo a seguir mostra como animar a posição de uma câmera e animar a direção em que ele está apontando em uma cena 3D.</span><span class="sxs-lookup"><span data-stu-id="9065a-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="9065a-104">Isso é feito por meio <xref:System.Windows.Media.Animation.Point3DAnimation> e <xref:System.Windows.Media.Animation.Vector3DAnimation> animar o <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> e <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> propriedades respectivamente do <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="9065a-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="9065a-105">Você pode usar uma animação como este para alterar de observador de uma cena em resposta a um evento.</span><span class="sxs-lookup"><span data-stu-id="9065a-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9065a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9065a-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9065a-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9065a-107">See also</span></span>

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [<span data-ttu-id="9065a-108">Animar a posição e a direção da câmera usando quadros principais</span><span class="sxs-lookup"><span data-stu-id="9065a-108">Animate Camera Position and Direction Using Key Frames</span></span>](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [<span data-ttu-id="9065a-109">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="9065a-109">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
