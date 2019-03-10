---
title: 'Como: Desenhar splines cardinais'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 687143273a07acba4b4d60acb1be25eee165b91d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710479"
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="02bd1-102">Como: Desenhar splines cardinais</span><span class="sxs-lookup"><span data-stu-id="02bd1-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="02bd1-103">Um spline cardinal é uma curva que passa suavemente por um determinado conjunto de pontos.</span><span class="sxs-lookup"><span data-stu-id="02bd1-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="02bd1-104">Para desenhar um spline cardinal, crie uma <xref:System.Drawing.Graphics> do objeto e passar o endereço de uma matriz de pontos para o <xref:System.Drawing.Graphics.DrawCurve%2A> método.</span><span class="sxs-lookup"><span data-stu-id="02bd1-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="02bd1-105">Desenhando um spline cardinal em forma de sino</span><span class="sxs-lookup"><span data-stu-id="02bd1-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="02bd1-106">O exemplo a seguir desenha um spline cardinal em forma de sino que passa por cinco pontos designados.</span><span class="sxs-lookup"><span data-stu-id="02bd1-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="02bd1-107">A ilustração a seguir mostra a curva e cinco pontos.</span><span class="sxs-lookup"><span data-stu-id="02bd1-107">The following illustration shows the curve and five points.</span></span>  
  
     <span data-ttu-id="02bd1-108">![Spline cardinal](./media/cardinalspline1.png "CardinalSpline1")</span><span class="sxs-lookup"><span data-stu-id="02bd1-108">![Cardinal Spline](./media/cardinalspline1.png "CardinalSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="02bd1-109">Desenhando um spline cardinal fechado</span><span class="sxs-lookup"><span data-stu-id="02bd1-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="02bd1-110">Use o <xref:System.Drawing.Graphics.DrawClosedCurve%2A> método da <xref:System.Drawing.Graphics> classe para desenhar um spline cardinal fechado.</span><span class="sxs-lookup"><span data-stu-id="02bd1-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="02bd1-111">Em um spline cardinal fechado, a curva continua durante o último ponto na matriz e se conecta com o primeiro ponto na matriz.</span><span class="sxs-lookup"><span data-stu-id="02bd1-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="02bd1-112">O exemplo a seguir desenha um spline cardinal fechado que passa por seis pontos designados.</span><span class="sxs-lookup"><span data-stu-id="02bd1-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="02bd1-113">A ilustração a seguir mostra o spline fechado junto com os seis pontos.</span><span class="sxs-lookup"><span data-stu-id="02bd1-113">The following illustration shows the closed spline along with the six points.</span></span>  
  
 <span data-ttu-id="02bd1-114">![Spline cardinal](./media/cardinalspline1a.png "CardinalSpline1A")</span><span class="sxs-lookup"><span data-stu-id="02bd1-114">![Cardinal Spline](./media/cardinalspline1a.png "CardinalSpline1A")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="02bd1-115">Alterando a curva de um spline cardinal</span><span class="sxs-lookup"><span data-stu-id="02bd1-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="02bd1-116">Alterar a maneira como um spline cardinal se dobra, passando um argumento de tensão para os <xref:System.Drawing.Graphics.DrawCurve%2A> método.</span><span class="sxs-lookup"><span data-stu-id="02bd1-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="02bd1-117">O exemplo a seguir desenha três splines cardinais que passam pelo mesmo conjunto de pontos.</span><span class="sxs-lookup"><span data-stu-id="02bd1-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="02bd1-118">A ilustração a seguir mostra os três splines junto com seus valores de tensão.</span><span class="sxs-lookup"><span data-stu-id="02bd1-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="02bd1-119">Observe que, quando a tensão for 0, os pontos são conectados por linhas retas.</span><span class="sxs-lookup"><span data-stu-id="02bd1-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 <span data-ttu-id="02bd1-120">![Spline cardinal](./media/cardinalspline2.png "CardinalSpline2")</span><span class="sxs-lookup"><span data-stu-id="02bd1-120">![Cardinal Spline](./media/cardinalspline2.png "CardinalSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02bd1-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="02bd1-121">Compiling the Code</span></span>  
 <span data-ttu-id="02bd1-122">Os exemplos anteriores são projetados para uso com o Windows Forms e exigem <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="02bd1-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02bd1-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02bd1-123">See also</span></span>
- [<span data-ttu-id="02bd1-124">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="02bd1-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="02bd1-125">Construir e Desenhar Curvas</span><span class="sxs-lookup"><span data-stu-id="02bd1-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
