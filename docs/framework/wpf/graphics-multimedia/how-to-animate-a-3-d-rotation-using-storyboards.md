---
title: 'Como: Animar uma rotação 3D usando storyboards'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112201"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a><span data-ttu-id="6af49-102">Como: Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="6af49-102">How to: Animate a 3D Rotation Using Storyboards</span></span>
<span data-ttu-id="6af49-103">O exemplo a seguir mostra como fazer um objeto 3D girar <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> enquanto <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> ele "oscila" animando as propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="6af49-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="6af49-104">Este <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto especifica a transformação de rotação do objeto 3D e, portanto, animar suas propriedades cria o efeito de rotação do desejo.</span><span class="sxs-lookup"><span data-stu-id="6af49-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="6af49-105">Dentro do <xref:System.Windows.Media.Animation.DoubleAnimation> Storyboard, é usado <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> para <xref:System.Windows.Media.Animation.Vector3DAnimation> animar a propriedade <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> enquanto é usado para animar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="6af49-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6af49-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6af49-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6af49-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="6af49-107">See also</span></span>

- [<span data-ttu-id="6af49-108">Animar uma rotação 3D usando rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="6af49-108">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="6af49-109">Animar uma rotação 3D usando quadros-chave (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="6af49-109">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="6af49-110">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="6af49-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="6af49-111">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="6af49-111">Storyboards Overview</span></span>](storyboards-overview.md)
