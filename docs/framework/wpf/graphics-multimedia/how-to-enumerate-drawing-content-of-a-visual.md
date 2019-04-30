---
title: 'Como: Enumerar conteúdo de desenho de um visual'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947466"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="dba21-102">Como: Enumerar conteúdo de desenho de um visual</span><span class="sxs-lookup"><span data-stu-id="dba21-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="dba21-103">O <xref:System.Windows.Media.Drawing> objeto fornece um modelo de objeto para enumerar o conteúdo de um <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="dba21-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dba21-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dba21-104">Example</span></span>  
 <span data-ttu-id="dba21-105">O exemplo a seguir usa o <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método para recuperar o <xref:System.Windows.Media.DrawingGroup> valor de um <xref:System.Windows.Media.Visual> e enumerá-lo.</span><span class="sxs-lookup"><span data-stu-id="dba21-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dba21-106">Quando você está enumerando o conteúdo do visual, você está recuperando <xref:System.Windows.Media.Drawing> objetos e não a representação subjacente dos dados de renderização como uma lista de instruções de gráficos de vetor.</span><span class="sxs-lookup"><span data-stu-id="dba21-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="dba21-107">Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dba21-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="dba21-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dba21-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="dba21-109">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="dba21-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="dba21-110">Visão geral de renderização de gráficos do WPF</span><span class="sxs-lookup"><span data-stu-id="dba21-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
