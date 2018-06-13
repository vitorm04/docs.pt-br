---
title: Como usar um desenho como uma origem de imagem
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 7da8a2a594b0562667aaf417d736159d98818a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562278"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="9e5a1-102">Como usar um desenho como uma origem de imagem</span><span class="sxs-lookup"><span data-stu-id="9e5a1-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="9e5a1-103">Este exemplo mostra como usar um <xref:System.Windows.Media.Drawing> como o <xref:System.Windows.Controls.Image.Source%2A> para um <xref:System.Windows.Controls.Image> controle.</span><span class="sxs-lookup"><span data-stu-id="9e5a1-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="9e5a1-104">Para exibir um <xref:System.Windows.Media.Drawing> com um <xref:System.Windows.Controls.Image> controlar, use um <xref:System.Windows.Media.DrawingImage> como o <xref:System.Windows.Controls.Image> do controle <xref:System.Windows.Controls.Image.Source%2A> e defina o <xref:System.Windows.Media.DrawingImage> do objeto <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> propriedade ao desenho que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="9e5a1-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e5a1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e5a1-105">Example</span></span>  
 <span data-ttu-id="9e5a1-106">O exemplo a seguir usa uma <xref:System.Windows.Media.DrawingImage> e um <xref:System.Windows.Controls.Image> controle para exibir um <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="9e5a1-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="9e5a1-107">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9e5a1-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="9e5a1-108">![Um GeometryDrawing de duas elipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="9e5a1-108">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="9e5a1-109">Uma DrawingImage</span><span class="sxs-lookup"><span data-stu-id="9e5a1-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9e5a1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e5a1-110">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="9e5a1-111">Desenhar uma imagem usando ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="9e5a1-111">Draw an Image Using ImageDrawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [<span data-ttu-id="9e5a1-112">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="9e5a1-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="9e5a1-113">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="9e5a1-113">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="9e5a1-114">Atributo PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="9e5a1-114">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
