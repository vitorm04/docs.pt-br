---
title: 'Como: Animar uma rotação 3D usando storyboards'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 20f5bf565ded624e4ea7e1e615f09b4c698526bd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357216"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="26ad3-102">Como: Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="26ad3-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="26ad3-103">O exemplo a seguir mostra como fazer com que um objeto 3D gire enquanto ele "vibra" pela animação a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> e <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> propriedades de um <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto.</span><span class="sxs-lookup"><span data-stu-id="26ad3-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="26ad3-104">Isso <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto Especifica a transformação de rotação do objeto 3D e portanto animando suas propriedades cria o efeito de rotação desejado.</span><span class="sxs-lookup"><span data-stu-id="26ad3-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="26ad3-105">Dentro do Storyboard <xref:System.Windows.Media.Animation.DoubleAnimation> é usado para animar a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> propriedade enquanto <xref:System.Windows.Media.Animation.Vector3DAnimation> é usado para animar o <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="26ad3-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26ad3-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26ad3-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="26ad3-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26ad3-107">See also</span></span>
- [<span data-ttu-id="26ad3-108">Animar uma rotação 3D usando Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="26ad3-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="26ad3-109">Animar uma rotação 3D usando quadros principais (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="26ad3-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="26ad3-110">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="26ad3-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="26ad3-111">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="26ad3-111">Storyboards Overview</span></span>](storyboards-overview.md)
