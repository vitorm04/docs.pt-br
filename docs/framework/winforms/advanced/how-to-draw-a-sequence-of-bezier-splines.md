---
title: 'Como: Desenhar uma sequência de B&#233;Splines de Bézier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 1de2f44be189cb2ff874a748ae6093c945120178
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711780"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="89e8c-102">Como: Desenhar uma sequência de B&#233;Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="89e8c-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="89e8c-103">Você pode usar o <xref:System.Drawing.Graphics.DrawBeziers%2A> método da <xref:System.Drawing.Graphics> conectado de classe para desenhar uma sequência de splines de Bézier.</span><span class="sxs-lookup"><span data-stu-id="89e8c-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89e8c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89e8c-104">Example</span></span>  
 <span data-ttu-id="89e8c-105">O exemplo a seguir desenha uma curva que consiste em dois splines de Bézier conectadas.</span><span class="sxs-lookup"><span data-stu-id="89e8c-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="89e8c-106">O ponto de extremidade da primeira spline de Bézier é o ponto de início da segunda spline de Bézier.</span><span class="sxs-lookup"><span data-stu-id="89e8c-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="89e8c-107">A ilustração a seguir mostra os conectados splines junto com os sete pontos.</span><span class="sxs-lookup"><span data-stu-id="89e8c-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="89e8c-108">![Bezier Spline](./media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="89e8c-108">![Bezier Spline](./media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89e8c-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="89e8c-109">Compiling the Code</span></span>  
 <span data-ttu-id="89e8c-110">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="89e8c-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e8c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89e8c-111">See also</span></span>
- [<span data-ttu-id="89e8c-112">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89e8c-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="89e8c-113">Splines de Bézier no GDI+</span><span class="sxs-lookup"><span data-stu-id="89e8c-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="89e8c-114">Construir e Desenhar Curvas</span><span class="sxs-lookup"><span data-stu-id="89e8c-114">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
