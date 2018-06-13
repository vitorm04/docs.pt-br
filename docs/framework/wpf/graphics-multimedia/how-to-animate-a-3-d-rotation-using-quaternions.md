---
title: Como animar uma rotação 3D usando Quaternions
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 4c2a46aad1feeefe5c7c31ec192f46b8c891337f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556933"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="ee569-102">Como animar uma rotação 3D usando Quaternions</span><span class="sxs-lookup"><span data-stu-id="ee569-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="ee569-103">Este exemplo mostra como animar uma rotação de um objeto 3D usando quatérnios.</span><span class="sxs-lookup"><span data-stu-id="ee569-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="ee569-104">O código a seguir mostra um <xref:System.Windows.Media.Media3D.QuaternionRotation3D> usado como o valor para o <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> propriedade de um <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="ee569-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="ee569-105">Isso <xref:System.Windows.Media.Media3D.QuaternionRotation3D> é animado com uma <xref:System.Windows.Media.Animation.QuaternionAnimation> dentro de um <xref:System.Windows.Media.Animation.Storyboard> usando o código abaixo.</span><span class="sxs-lookup"><span data-stu-id="ee569-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="ee569-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee569-106">Example</span></span>  
 <span data-ttu-id="ee569-107">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="ee569-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ee569-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee569-108">See Also</span></span>  
 [<span data-ttu-id="ee569-109">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="ee569-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="ee569-110">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="ee569-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="ee569-111">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="ee569-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="ee569-112">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="ee569-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="ee569-113">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="ee569-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="ee569-114">Animar uma rotação 3D usando Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="ee569-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
