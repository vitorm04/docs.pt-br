---
title: 'Como: Animar uma rotação 3D usando quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: d994ac2ae67fd366f27f123d5bd15f14d5ac7abe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183216"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="3e7c6-102">Como: Animar uma rotação 3D usando quaternions</span><span class="sxs-lookup"><span data-stu-id="3e7c6-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="3e7c6-103">Este exemplo mostra como animar uma rotação de um objeto 3D usando quaternions.</span><span class="sxs-lookup"><span data-stu-id="3e7c6-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="3e7c6-104">O código a seguir mostra uma <xref:System.Windows.Media.Media3D.QuaternionRotation3D> usado como o valor para o <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> propriedade de um <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="3e7c6-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="3e7c6-105">Isso <xref:System.Windows.Media.Media3D.QuaternionRotation3D> é animado com uma <xref:System.Windows.Media.Animation.QuaternionAnimation> dentro de um <xref:System.Windows.Media.Animation.Storyboard> usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3e7c6-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="3e7c6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e7c6-106">Example</span></span>  
 <span data-ttu-id="3e7c6-107">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="3e7c6-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3e7c6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e7c6-108">See also</span></span>

- [<span data-ttu-id="3e7c6-109">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="3e7c6-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="3e7c6-110">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="3e7c6-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="3e7c6-111">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="3e7c6-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="3e7c6-112">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="3e7c6-112">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="3e7c6-113">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="3e7c6-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="3e7c6-114">Animar uma rotação 3D usando Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="3e7c6-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
