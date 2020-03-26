---
title: 'Como: Aplicar material na frente e atrás de um objeto 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112135"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a><span data-ttu-id="a5775-102">Como: Aplicar material na frente e atrás de um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="a5775-102">How to: Apply Material to the Front and Back of a 3D Object</span></span>
<span data-ttu-id="a5775-103">O exemplo a seguir <xref:System.Windows.Media.Media3D.Material> mostra como aplicar um na frente e atrás de um objeto 3D e animar o objeto para mostrar ambos os lados do objeto.</span><span class="sxs-lookup"><span data-stu-id="a5775-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="a5775-104">A <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriedade <xref:System.Windows.Media.Media3D.GeometryModel3D> de a é <xref:System.Windows.Media.Brush> usada para aplicar um vermelho <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> na <xref:System.Windows.Media.Media3D.GeometryModel3D> parte frontal do <xref:System.Windows.Media.Brush> objeto e a propriedade do é usada para aplicar um azul na parte traseira do objeto.</span><span class="sxs-lookup"><span data-stu-id="a5775-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="a5775-105">O código abaixo mostra a aplicação dos materiais ao objeto:</span><span class="sxs-lookup"><span data-stu-id="a5775-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="a5775-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5775-106">Example</span></span>  
 <span data-ttu-id="a5775-107">O código a seguir mostra toda a amostra.</span><span class="sxs-lookup"><span data-stu-id="a5775-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a5775-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5775-108">See also</span></span>

- [<span data-ttu-id="a5775-109">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="a5775-109">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="a5775-110">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="a5775-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="a5775-111">Propriedades de material animado em uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="a5775-111">Animate Material Properties in a 3D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="a5775-112">Aplique material emissivo a um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="a5775-112">Apply Emissive Material to a 3D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
