---
title: Como desenhar uma linha
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452942"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="45a64-102">Como desenhar uma linha</span><span class="sxs-lookup"><span data-stu-id="45a64-102">How to: Draw a Line</span></span>
<span data-ttu-id="45a64-103">Este exemplo mostra como desenhar linhas usando o elemento <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="45a64-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="45a64-104">Para desenhar uma linha, crie um elemento <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="45a64-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="45a64-105">Use suas propriedades <xref:System.Windows.Shapes.Line.X1%2A> e <xref:System.Windows.Shapes.Line.Y1%2A> para definir seu ponto de partida; e use suas propriedades <xref:System.Windows.Shapes.Line.X2%2A> e <xref:System.Windows.Shapes.Line.Y2%2A> para definir seu ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="45a64-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="45a64-106">Por fim, defina seu <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> porque uma linha sem um traço é invisível.</span><span class="sxs-lookup"><span data-stu-id="45a64-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="45a64-107">A definição do elemento <xref:System.Windows.Shapes.Shape.Fill%2A> para uma linha não tem efeito, pois uma linha não tem interior.</span><span class="sxs-lookup"><span data-stu-id="45a64-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="45a64-108">O exemplo a seguir desenha três linhas dentro de um elemento <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="45a64-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45a64-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45a64-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="45a64-110">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="45a64-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a64-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="45a64-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="45a64-112">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="45a64-112">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
