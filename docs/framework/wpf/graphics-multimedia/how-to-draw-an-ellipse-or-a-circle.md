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
ms.openlocfilehash: ddeada8619d1b6c8970f1efb7cca1bc98773d0c5
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003939"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="41a5a-102">Como desenhar uma elipse ou um círculo</span><span class="sxs-lookup"><span data-stu-id="41a5a-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="41a5a-103">Este exemplo mostra como desenhar elipses e círculos usando o <xref:System.Windows.Shapes.Ellipse> elemento.</span><span class="sxs-lookup"><span data-stu-id="41a5a-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="41a5a-104">Para desenhar uma elipse, crie uma <xref:System.Windows.Shapes.Ellipse> elemento e especifique seus <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="41a5a-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="41a5a-105">Use sua <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade para especificar o <xref:System.Windows.Media.Brush> que é usado para pintar o interior da elipse.</span><span class="sxs-lookup"><span data-stu-id="41a5a-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="41a5a-106">Use sua <xref:System.Windows.Shapes.Shape.Stroke%2A> propriedade para especificar o <xref:System.Windows.Media.Brush> que é usado para pintar o contorno da elipse.</span><span class="sxs-lookup"><span data-stu-id="41a5a-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="41a5a-107">O <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedade especifica a espessura do contorno elipse.</span><span class="sxs-lookup"><span data-stu-id="41a5a-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="41a5a-108">Para desenhar um círculo, faça o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> da <xref:System.Windows.Shapes.Ellipse> elemento igual entre si.</span><span class="sxs-lookup"><span data-stu-id="41a5a-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="41a5a-109">O exemplo a seguir desenha quatro <xref:System.Windows.Shapes.Ellipse> elementos dentro de um <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="41a5a-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41a5a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41a5a-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="41a5a-111">Embora este exemplo usa uma <xref:System.Windows.Controls.Canvas> para conter as elipses, você pode usar elementos de elipse (e todos os outros elementos de forma) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que dá suporte a conteúdo não textual.</span><span class="sxs-lookup"><span data-stu-id="41a5a-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="41a5a-112">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="41a5a-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a5a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41a5a-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="41a5a-114">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="41a5a-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
