---
title: Como desenhar um retângulo
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452929"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="1fe30-102">Como desenhar um retângulo</span><span class="sxs-lookup"><span data-stu-id="1fe30-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="1fe30-103">Este exemplo mostra como desenhar um retângulo usando o elemento <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="1fe30-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="1fe30-104">Para desenhar um retângulo, crie um elemento <xref:System.Windows.Shapes.Rectangle> e especifique seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fe30-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="1fe30-105">Para pintar o interior do retângulo, defina seu <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fe30-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="1fe30-106">Para dar um esboço ao retângulo, use suas propriedades <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fe30-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="1fe30-107">Para dar os cantos arredondados do retângulo, especifique as propriedades opcionais <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fe30-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="1fe30-108">As propriedades <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> definem o raios do eixo x e do eixo y da elipse que é usada para arredondar os cantos do retângulo.</span><span class="sxs-lookup"><span data-stu-id="1fe30-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="1fe30-109">No exemplo a seguir, dois elementos de <xref:System.Windows.Shapes.Rectangle> são desenhados em um <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="1fe30-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="1fe30-110">O primeiro retângulo tem um <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span><span class="sxs-lookup"><span data-stu-id="1fe30-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="1fe30-111">O segundo retângulo tem um <xref:System.Windows.Media.Brushes.Blue%2A> interior, uma estrutura de tópicos <xref:System.Windows.Media.Brushes.Black%2A> e cantos arredondados.</span><span class="sxs-lookup"><span data-stu-id="1fe30-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fe30-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fe30-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="1fe30-113">Embora este exemplo use um <xref:System.Windows.Controls.Canvas> para conter os retângulos, você pode usar elementos Rectangle (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que ofereça suporte a conteúdo que não seja de texto.</span><span class="sxs-lookup"><span data-stu-id="1fe30-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="1fe30-114">Na verdade, os retângulos são particularmente úteis para fornecer planos de fundo para partes de <xref:System.Windows.Controls.Grid> painéis.</span><span class="sxs-lookup"><span data-stu-id="1fe30-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="1fe30-115">Para ver um exemplo, consulte a [Visão geral da tabela](../advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1fe30-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="1fe30-116">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="1fe30-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe30-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="1fe30-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="1fe30-118">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="1fe30-118">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="1fe30-119">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="1fe30-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="1fe30-120">Visão Geral da Tabela</span><span class="sxs-lookup"><span data-stu-id="1fe30-120">Table Overview</span></span>](../advanced/table-overview.md)
