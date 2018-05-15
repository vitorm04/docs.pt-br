---
title: Polígonos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 3ac6b9b651e65a45612cf2bd8ff17990c5cfba0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="baf37-102">Polígonos no GDI+</span><span class="sxs-lookup"><span data-stu-id="baf37-102">Polygons in GDI+</span></span>
<span data-ttu-id="baf37-103">Um polígono é uma forma fechada com três ou mais lados retos.</span><span class="sxs-lookup"><span data-stu-id="baf37-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="baf37-104">Por exemplo, um triângulo é um polígono com três lados, um retângulo é um polígono com quatro lados e um Pentágono é um polígono com cinco lados.</span><span class="sxs-lookup"><span data-stu-id="baf37-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="baf37-105">A ilustração a seguir mostra diversos polígonos.</span><span class="sxs-lookup"><span data-stu-id="baf37-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="baf37-106">![Polígonos](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="baf37-106">![Polygons](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="baf37-107">Desenhando um polígono</span><span class="sxs-lookup"><span data-stu-id="baf37-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="baf37-108">Para desenhar um polígono, é necessário um <xref:System.Drawing.Graphics> objeto, um <xref:System.Drawing.Pen> objeto e uma matriz de <xref:System.Drawing.Point> (ou <xref:System.Drawing.PointF>) objetos.</span><span class="sxs-lookup"><span data-stu-id="baf37-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="baf37-109">O <xref:System.Drawing.Graphics> objeto fornece o <xref:System.Drawing.Graphics.DrawPolygon%2A> método.</span><span class="sxs-lookup"><span data-stu-id="baf37-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="baf37-110">O <xref:System.Drawing.Pen> objeto armazena atributos, como a largura e a cor da linha usada para renderizar o polígono e a matriz de <xref:System.Drawing.Point> objetos armazena os pontos conectados por linhas retas.</span><span class="sxs-lookup"><span data-stu-id="baf37-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="baf37-111">O <xref:System.Drawing.Pen> objeto e a matriz de <xref:System.Drawing.Point> objetos são transmitidos como argumentos para o <xref:System.Drawing.Graphics.DrawPolygon%2A> método.</span><span class="sxs-lookup"><span data-stu-id="baf37-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="baf37-112">O exemplo a seguir desenha um polígono com três lados.</span><span class="sxs-lookup"><span data-stu-id="baf37-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="baf37-113">Observe que há apenas três pontos em `myPointArray`: (0, 0), (50, 30) e (30, 60).</span><span class="sxs-lookup"><span data-stu-id="baf37-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="baf37-114">O <xref:System.Drawing.Graphics.DrawPolygon%2A> método fecha automaticamente o polígono ao desenhar uma linha de (30, 60) para o ponto de partida (0, 0).</span><span class="sxs-lookup"><span data-stu-id="baf37-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="baf37-115">A ilustração a seguir mostra o polígono.</span><span class="sxs-lookup"><span data-stu-id="baf37-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="baf37-116">![Polígono](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="baf37-116">![Polygon](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf37-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baf37-117">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="baf37-118">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="baf37-118">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="baf37-119">Como criar uma caneta</span><span class="sxs-lookup"><span data-stu-id="baf37-119">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
