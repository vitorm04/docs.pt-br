---
title: Como desenhar uma elipse ou um círculo
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452916"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="cf90f-102">Como desenhar uma elipse ou um círculo</span><span class="sxs-lookup"><span data-stu-id="cf90f-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="cf90f-103">Este exemplo mostra como desenhar reticências e círculos usando o elemento <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="cf90f-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="cf90f-104">Para desenhar uma elipse, crie um elemento <xref:System.Windows.Shapes.Ellipse> e especifique seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf90f-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="cf90f-105">Use sua propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> para especificar o <xref:System.Windows.Media.Brush> usado para pintar o interior da elipse.</span><span class="sxs-lookup"><span data-stu-id="cf90f-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="cf90f-106">Use sua propriedade <xref:System.Windows.Shapes.Shape.Stroke%2A> para especificar o <xref:System.Windows.Media.Brush> usado para pintar o contorno da elipse.</span><span class="sxs-lookup"><span data-stu-id="cf90f-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="cf90f-107">A propriedade <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> especifica a espessura da estrutura de tópicos da elipse.</span><span class="sxs-lookup"><span data-stu-id="cf90f-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="cf90f-108">Para desenhar um círculo, torne o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> do elemento <xref:System.Windows.Shapes.Ellipse> igual um do outro.</span><span class="sxs-lookup"><span data-stu-id="cf90f-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="cf90f-109">O exemplo a seguir desenha quatro elementos <xref:System.Windows.Shapes.Ellipse> dentro de um <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="cf90f-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf90f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf90f-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="cf90f-111">Embora este exemplo use um <xref:System.Windows.Controls.Canvas> para conter as reticências, você pode usar elementos Ellipse (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que ofereça suporte a conteúdo que não seja de texto.</span><span class="sxs-lookup"><span data-stu-id="cf90f-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="cf90f-112">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="cf90f-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf90f-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf90f-113">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="cf90f-114">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="cf90f-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
