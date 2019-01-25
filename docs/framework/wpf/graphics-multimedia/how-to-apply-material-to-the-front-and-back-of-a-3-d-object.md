---
title: 'Como: Aplicar material à frente e ao verso de um objeto 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 16f30e3a880d7dcc943a9583ba0f04c4bd682827
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652027"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="3f01c-102">Como: Aplicar material à frente e ao verso de um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="3f01c-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="3f01c-103">O exemplo a seguir mostra como aplicar um <xref:System.Windows.Media.Media3D.Material> do objeto para a frente e ao verso de um 3D e animar o objeto para mostrar ambos os lados do objeto.</span><span class="sxs-lookup"><span data-stu-id="3f01c-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="3f01c-104">O <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D> é usado para aplicar um vermelho <xref:System.Windows.Media.Brush> ao lado frontal do objeto e o <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> propriedade do <xref:System.Windows.Media.Media3D.GeometryModel3D> é usado para aplicar uma azul <xref:System.Windows.Media.Brush> para a parte de trás do objeto.</span><span class="sxs-lookup"><span data-stu-id="3f01c-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="3f01c-105">O código a seguir mostra o aplicativo de materiais para o objeto:</span><span class="sxs-lookup"><span data-stu-id="3f01c-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="3f01c-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f01c-106">Example</span></span>  
 <span data-ttu-id="3f01c-107">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="3f01c-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3f01c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f01c-108">See also</span></span>
- [<span data-ttu-id="3f01c-109">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="3f01c-109">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="3f01c-110">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="3f01c-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="3f01c-111">Animar propriedades de material em uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="3f01c-111">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="3f01c-112">Aplicar material emissivo a um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="3f01c-112">Apply Emissive Material to a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
