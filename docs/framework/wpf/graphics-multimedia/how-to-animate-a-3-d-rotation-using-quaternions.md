---
title: 'Como: Animar uma rotação 3D usando quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112239"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a><span data-ttu-id="126aa-102">Como: Animar uma rotação 3D usando quaternions</span><span class="sxs-lookup"><span data-stu-id="126aa-102">How to: Animate a 3D Rotation Using Quaternions</span></span>
<span data-ttu-id="126aa-103">Este exemplo mostra como animar uma rotação de um objeto 3D usando quaternions.</span><span class="sxs-lookup"><span data-stu-id="126aa-103">This example shows how to animate a rotation of a 3D object using quaternions.</span></span>  
  
 <span data-ttu-id="126aa-104">O código abaixo <xref:System.Windows.Media.Media3D.QuaternionRotation3D> mostra um usado <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> como <xref:System.Windows.Media.Media3D.RotateTransform3D>o valor para a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="126aa-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="126aa-105">Este <xref:System.Windows.Media.Media3D.QuaternionRotation3D> é animado <xref:System.Windows.Media.Animation.QuaternionAnimation> com <xref:System.Windows.Media.Animation.Storyboard> um dentro de um usando o código abaixo.</span><span class="sxs-lookup"><span data-stu-id="126aa-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="126aa-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="126aa-106">Example</span></span>  
 <span data-ttu-id="126aa-107">O código a seguir mostra toda a amostra.</span><span class="sxs-lookup"><span data-stu-id="126aa-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="126aa-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="126aa-108">See also</span></span>

- [<span data-ttu-id="126aa-109">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="126aa-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="126aa-110">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="126aa-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="126aa-111">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="126aa-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="126aa-112">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="126aa-112">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="126aa-113">Animar uma rotação 3D usando storyboards</span><span class="sxs-lookup"><span data-stu-id="126aa-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="126aa-114">Animar uma rotação 3D usando rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="126aa-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
