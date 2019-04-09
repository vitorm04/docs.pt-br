---
title: 'Como: Usar um desenho como uma fonte de imagem'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097854"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="9ce77-102">Como: Usar um desenho como uma fonte de imagem</span><span class="sxs-lookup"><span data-stu-id="9ce77-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="9ce77-103">Este exemplo mostra como usar um <xref:System.Windows.Media.Drawing> como o <xref:System.Windows.Controls.Image.Source%2A> para um <xref:System.Windows.Controls.Image> controle.</span><span class="sxs-lookup"><span data-stu-id="9ce77-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="9ce77-104">Para exibir uma <xref:System.Windows.Media.Drawing> com um <xref:System.Windows.Controls.Image> controlar, use um <xref:System.Windows.Media.DrawingImage> como o <xref:System.Windows.Controls.Image> do controle <xref:System.Windows.Controls.Image.Source%2A> e defina a <xref:System.Windows.Media.DrawingImage> do objeto <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> propriedade para o desenho que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="9ce77-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce77-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ce77-105">Example</span></span>  
 <span data-ttu-id="9ce77-106">O exemplo a seguir usa uma <xref:System.Windows.Media.DrawingImage> e uma <xref:System.Windows.Controls.Image> controle para exibir um <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="9ce77-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="9ce77-107">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9ce77-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="9ce77-108">![Um GeometryDrawing de duas elipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="9ce77-108">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="9ce77-109">Uma DrawingImage</span><span class="sxs-lookup"><span data-stu-id="9ce77-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9ce77-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ce77-110">See also</span></span>

- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="9ce77-111">Desenhar uma imagem usando ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="9ce77-111">Draw an Image Using ImageDrawing</span></span>](how-to-draw-an-image-using-imagedrawing.md)
- [<span data-ttu-id="9ce77-112">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="9ce77-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="9ce77-113">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="9ce77-113">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="9ce77-114">Atributo PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="9ce77-114">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
