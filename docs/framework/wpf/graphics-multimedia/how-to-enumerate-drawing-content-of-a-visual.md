---
title: 'Como: Enumerar conteúdo de desenho de um visual'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930077"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="2aef4-102">Como: Enumerar conteúdo de desenho de um visual</span><span class="sxs-lookup"><span data-stu-id="2aef4-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="2aef4-103">O <xref:System.Windows.Media.Drawing> objeto fornece um modelo de objeto para enumerar o conteúdo de <xref:System.Windows.Media.Visual>um.</span><span class="sxs-lookup"><span data-stu-id="2aef4-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aef4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2aef4-104">Example</span></span>  
 <span data-ttu-id="2aef4-105">O exemplo a seguir usa <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> o método para recuperar <xref:System.Windows.Media.DrawingGroup> o valor de <xref:System.Windows.Media.Visual> a e enumerá-lo.</span><span class="sxs-lookup"><span data-stu-id="2aef4-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2aef4-106">Ao enumerar o conteúdo do Visual, você está recuperando <xref:System.Windows.Media.Drawing> objetos e não a representação subjacente da lista de instruções de renderização de dados como elementos gráficos de vetor.</span><span class="sxs-lookup"><span data-stu-id="2aef4-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="2aef4-107">Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2aef4-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="2aef4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2aef4-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="2aef4-109">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="2aef4-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="2aef4-110">Visão geral de renderização de gráficos do WPF</span><span class="sxs-lookup"><span data-stu-id="2aef4-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
