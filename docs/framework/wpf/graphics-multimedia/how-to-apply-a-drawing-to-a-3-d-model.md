---
title: 'Como: Aplicar um desenho a um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: a20b89a7359fc85d9790ac02dd2b173452df8c22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125028"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="a32bb-102">Como: Aplicar um desenho a um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="a32bb-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="a32bb-103">Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> como o <xref:System.Windows.Media.Media3D.Material> aplicados a um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.</span><span class="sxs-lookup"><span data-stu-id="a32bb-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="a32bb-104">O código a seguir define uma <xref:System.Windows.Media.DrawingGroup> como o conteúdo de um <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="a32bb-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="a32bb-105">O <xref:System.Windows.Media.DrawingBrush> é definido como o <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriedade da <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plano.</span><span class="sxs-lookup"><span data-stu-id="a32bb-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="a32bb-106">**Observação:** Muitas vezes é desejável para definir objetos complexos e valores, como o desenho abaixo como recursos que podem ser reutilizados e simplificam seu código.</span><span class="sxs-lookup"><span data-stu-id="a32bb-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="a32bb-107">Ver [recursos XAML](../advanced/xaml-resources.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="a32bb-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="a32bb-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a32bb-108">Example</span></span>  
 <span data-ttu-id="a32bb-109">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="a32bb-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a32bb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a32bb-110">See also</span></span>

- [<span data-ttu-id="a32bb-111">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="a32bb-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="a32bb-112">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="a32bb-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="a32bb-113">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="a32bb-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="a32bb-114">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="a32bb-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
