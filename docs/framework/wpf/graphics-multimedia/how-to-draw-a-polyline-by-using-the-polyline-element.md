---
title: Como desenhar uma polilinha usando o elemento Polyline
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452955"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="5fa7a-102">Como desenhar uma polilinha usando o elemento Polyline</span><span class="sxs-lookup"><span data-stu-id="5fa7a-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="5fa7a-103">Este exemplo mostra como desenhar uma polilinha, que é uma série de linhas conectadas, usando o elemento <xref:System.Windows.Shapes.Polyline>.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="5fa7a-104">Para desenhar uma polilinha, crie um elemento <xref:System.Windows.Shapes.Polyline> e use sua propriedade <xref:System.Windows.Shapes.Polyline.Points%2A> para especificar os vértices de forma.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="5fa7a-105">Por fim, use as propriedades <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> para descrever o contorno de polilinha porque uma linha sem um traço é invisível.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fa7a-106">Como o elemento <xref:System.Windows.Shapes.Polyline> não é uma forma fechada, a propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> não tem efeito, mesmo que você feche deliberadamente o contorno da forma.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="5fa7a-107">Para criar uma forma fechada com um <xref:System.Windows.Shapes.Shape.Fill%2A>, use um elemento <xref:System.Windows.Shapes.Polygon>.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="5fa7a-108">O exemplo a seguir desenha dois elementos <xref:System.Windows.Shapes.Polyline> dentro de um <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa7a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fa7a-109">Example</span></span>  
 <span data-ttu-id="5fa7a-110">Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="5fa7a-111">Embora este exemplo use uma <xref:System.Windows.Controls.Canvas> para conter as polilinhas, você pode usar elementos Polyline (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que ofereça suporte a conteúdo que não seja de texto.</span><span class="sxs-lookup"><span data-stu-id="5fa7a-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="5fa7a-112">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="5fa7a-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa7a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="5fa7a-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="5fa7a-114">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="5fa7a-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="5fa7a-115">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="5fa7a-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
