---
title: 'Como: Desenhar um único B&#233;Spline de Bézier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 32fc09c7525b40daea8c8705c43100cea0c052bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676452"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="2bcdd-102">Como: Desenhar um único B&#233;Spline de Bézier</span><span class="sxs-lookup"><span data-stu-id="2bcdd-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="2bcdd-103">Uma spline de Bézier é definida por quatro pontos: um ponto de início, dois pontos de controle e um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2bcdd-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bcdd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bcdd-104">Example</span></span>  
 <span data-ttu-id="2bcdd-105">O exemplo a seguir desenha uma spline de Bézier com ponto de partida (10, 100) e o ponto de extremidade (200, 100).</span><span class="sxs-lookup"><span data-stu-id="2bcdd-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="2bcdd-106">Pontos de controle são (100, 10) e (150, 150).</span><span class="sxs-lookup"><span data-stu-id="2bcdd-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="2bcdd-107">A ilustração a seguir mostra o spline de Bézier resultante junto com seu ponto inicial, a pontos de controle e o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2bcdd-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="2bcdd-108">A ilustração também mostra envoltória convexa o spline, que é um polígono formado conectando-se em quatro pontos com linhas retas.</span><span class="sxs-lookup"><span data-stu-id="2bcdd-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="2bcdd-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="2bcdd-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2bcdd-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2bcdd-110">Compiling the Code</span></span>  
 <span data-ttu-id="2bcdd-111">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="2bcdd-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcdd-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bcdd-112">See also</span></span>
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [<span data-ttu-id="2bcdd-113">Splines de Bézier no GDI+</span><span class="sxs-lookup"><span data-stu-id="2bcdd-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)
- [<span data-ttu-id="2bcdd-114">Como: Desenhar uma sequência de Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="2bcdd-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
