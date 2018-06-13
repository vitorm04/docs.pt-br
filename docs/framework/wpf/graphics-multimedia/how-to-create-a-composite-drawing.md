---
title: Como criar um desenho composto
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: bb222fff11c81b491c0413f174539ff0005d11b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561573"
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="ab45e-102">Como criar um desenho composto</span><span class="sxs-lookup"><span data-stu-id="ab45e-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="ab45e-103">Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingGroup> para criar desenhos complexos combinando vários <xref:System.Windows.Media.Drawing> objetos em um único desenho composto.</span><span class="sxs-lookup"><span data-stu-id="ab45e-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab45e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab45e-104">Example</span></span>  
 <span data-ttu-id="ab45e-105">O exemplo a seguir usa uma <xref:System.Windows.Media.DrawingGroup> para criar um desenho composto a partir de <xref:System.Windows.Media.GeometryDrawing> e <xref:System.Windows.Media.ImageDrawing> objetos.</span><span class="sxs-lookup"><span data-stu-id="ab45e-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="ab45e-106">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="ab45e-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="ab45e-107">![Um DrawingGroup com vários desenhos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="ab45e-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="ab45e-108">Um desenho composto criado usando DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="ab45e-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="ab45e-109">Observe a borda cinza, que mostra os limites do desenho.</span><span class="sxs-lookup"><span data-stu-id="ab45e-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="ab45e-110">Você pode usar um <xref:System.Windows.Media.DrawingGroup> para aplicar uma <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> configuração, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, ou <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> para desenhos que ele contém.</span><span class="sxs-lookup"><span data-stu-id="ab45e-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="ab45e-111">Porque um <xref:System.Windows.Media.DrawingGroup> também é um <xref:System.Windows.Media.Drawing>, ele pode conter outros <xref:System.Windows.Media.DrawingGroup> objetos.</span><span class="sxs-lookup"><span data-stu-id="ab45e-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="ab45e-112">O exemplo a seguir é semelhante ao exemplo anterior, exceto que ele usa adicionais <xref:System.Windows.Media.DrawingGroup> objetos para aplicar efeitos de bitmap e uma máscara de opacidade a alguns dos seus desenhos.</span><span class="sxs-lookup"><span data-stu-id="ab45e-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="ab45e-113">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="ab45e-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="ab45e-114">![Um DrawingGroup com vários desenhos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="ab45e-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="ab45e-115">Desenho composto que tem vários objetos DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="ab45e-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="ab45e-116">Observe a borda cinza, que mostra os limites do desenho.</span><span class="sxs-lookup"><span data-stu-id="ab45e-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="ab45e-117">Para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos, consulte [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ab45e-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab45e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab45e-118">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [<span data-ttu-id="ab45e-119">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="ab45e-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
