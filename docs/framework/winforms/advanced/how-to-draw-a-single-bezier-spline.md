---
title: 'Como: Desenhar uma única B&#233;zier Spline'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 9e91b63275c37fc0cdde5721fddd114e1bf2264e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521330"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="b204a-102">Como: Desenhar uma única B&#233;zier Spline</span><span class="sxs-lookup"><span data-stu-id="b204a-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="b204a-103">Uma spline de Bézier é definida por quatro pontos: um ponto inicial, dois pontos de controle e um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b204a-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b204a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b204a-104">Example</span></span>  
 <span data-ttu-id="b204a-105">O exemplo a seguir desenha um spline de Bézier com o ponto inicial (10, 100) e o ponto de extremidade (200, 100).</span><span class="sxs-lookup"><span data-stu-id="b204a-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="b204a-106">O controle pontos são (100, 10) e (150, 150).</span><span class="sxs-lookup"><span data-stu-id="b204a-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="b204a-107">A ilustração a seguir mostra o spline de Bézier resultante juntamente com seu ponto inicial, a pontos de controle e o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b204a-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="b204a-108">A ilustração também mostra forma convexa os spline, que é um polígono formado conectando os quatro pontos com linhas retas.</span><span class="sxs-lookup"><span data-stu-id="b204a-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="b204a-109">![Os Spline de Bézier](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="b204a-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b204a-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b204a-110">Compiling the Code</span></span>  
 <span data-ttu-id="b204a-111">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b204a-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b204a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b204a-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [<span data-ttu-id="b204a-113">Splines de Bézier no GDI+</span><span class="sxs-lookup"><span data-stu-id="b204a-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="b204a-114">Como Desenhar uma Sequência de Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="b204a-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
