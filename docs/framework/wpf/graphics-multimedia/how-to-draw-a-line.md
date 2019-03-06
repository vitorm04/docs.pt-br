---
title: 'Como: Desenhar uma linha'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a194fad5471cafcb567aa00522a597a4186ef4af
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374174"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="d82b8-102">Como: Desenhar uma linha</span><span class="sxs-lookup"><span data-stu-id="d82b8-102">How to: Draw a Line</span></span>
<span data-ttu-id="d82b8-103">Este exemplo mostra como desenhar linhas, usando o <xref:System.Windows.Shapes.Line> elemento.</span><span class="sxs-lookup"><span data-stu-id="d82b8-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="d82b8-104">Para desenhar uma linha, crie um <xref:System.Windows.Shapes.Line> elemento.</span><span class="sxs-lookup"><span data-stu-id="d82b8-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="d82b8-105">Use sua <xref:System.Windows.Shapes.Line.X1%2A> e <xref:System.Windows.Shapes.Line.Y1%2A> propriedades para definir seu ponto inicial; e use seu <xref:System.Windows.Shapes.Line.X2%2A> e <xref:System.Windows.Shapes.Line.Y2%2A> propriedades para definir seu ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d82b8-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="d82b8-106">Por fim, defina suas <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> porque uma linha sem traço é invisível.</span><span class="sxs-lookup"><span data-stu-id="d82b8-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="d82b8-107">Definindo o <xref:System.Windows.Shapes.Shape.Fill%2A> elemento para uma linha não tem nenhum efeito, porque uma linha não possui interior.</span><span class="sxs-lookup"><span data-stu-id="d82b8-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="d82b8-108">O exemplo a seguir desenha três linhas dentro um <xref:System.Windows.Controls.Canvas> elemento.</span><span class="sxs-lookup"><span data-stu-id="d82b8-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d82b8-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d82b8-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="d82b8-110">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="d82b8-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82b8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d82b8-111">See also</span></span>
- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="d82b8-112">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="d82b8-112">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
