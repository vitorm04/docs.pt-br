---
title: Como aplicar um desenho a um modelo 3D
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 26a84d963cac3b5c23617bfaa23279021e29c07a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559048"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="121c6-102">Como aplicar um desenho a um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="121c6-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="121c6-103">Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> como o <xref:System.Windows.Media.Media3D.Material> aplicado a um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.</span><span class="sxs-lookup"><span data-stu-id="121c6-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="121c6-104">O código a seguir define uma <xref:System.Windows.Media.DrawingGroup> como o conteúdo de um <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="121c6-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="121c6-105">O <xref:System.Windows.Media.DrawingBrush> é definido como o <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriedade do <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plano.</span><span class="sxs-lookup"><span data-stu-id="121c6-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="121c6-106">**Observação:** geralmente é desejável para definir objetos complexos e valores, como o desenho abaixo como recursos que podem ser reutilizados e simplificam seu código.</span><span class="sxs-lookup"><span data-stu-id="121c6-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="121c6-107">Consulte [recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="121c6-107">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="121c6-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="121c6-108">Example</span></span>  
 <span data-ttu-id="121c6-109">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="121c6-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="121c6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="121c6-110">See Also</span></span>  
 [<span data-ttu-id="121c6-111">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="121c6-111">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="121c6-112">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="121c6-112">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="121c6-113">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="121c6-113">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="121c6-114">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="121c6-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
