---
title: Curvas abertas e fechadas no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 8581b5f8d774a91d17dcfe93f801d87394f28c0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735202"
---
# <a name="open-and-closed-curves-in-gdi"></a><span data-ttu-id="91cbb-102">Curvas abertas e fechadas no GDI+</span><span class="sxs-lookup"><span data-stu-id="91cbb-102">Open and Closed Curves in GDI+</span></span>
<span data-ttu-id="91cbb-103">A ilustração a seguir mostra duas curvas: uma aberta e outra fechada.</span><span class="sxs-lookup"><span data-stu-id="91cbb-103">The following illustration shows two curves: one open and one closed.</span></span>  
  
 <span data-ttu-id="91cbb-104">![Curvas abertas e fechadas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span><span class="sxs-lookup"><span data-stu-id="91cbb-104">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span></span>  
  
## <a name="managed-interface-for-curves"></a><span data-ttu-id="91cbb-105">Interface gerenciada para curvas</span><span class="sxs-lookup"><span data-stu-id="91cbb-105">Managed Interface for Curves</span></span>  
 <span data-ttu-id="91cbb-106">Curvas fechadas têm um interior e, portanto, podem ser preenchidas com um pincel.</span><span class="sxs-lookup"><span data-stu-id="91cbb-106">Closed curves have an interior and therefore can be filled with a brush.</span></span> <span data-ttu-id="91cbb-107">O <xref:System.Drawing.Graphics> classe [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece os seguintes métodos para preencher as curvas e formas fechadas: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, e <xref:System.Drawing.Graphics.FillRegion%2A>.</span><span class="sxs-lookup"><span data-stu-id="91cbb-107">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for filling closed shapes and curves: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, and <xref:System.Drawing.Graphics.FillRegion%2A>.</span></span> <span data-ttu-id="91cbb-108">Sempre que você chama um desses métodos, você deve passar um dos tipos específicos de pincel (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ou <xref:System.Drawing.Drawing2D.PathGradientBrush>) como um argumento.</span><span class="sxs-lookup"><span data-stu-id="91cbb-108">Whenever you call one of these methods, you must pass one of the specific brush types (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, or <xref:System.Drawing.Drawing2D.PathGradientBrush>) as an argument.</span></span>  
  
 <span data-ttu-id="91cbb-109">O <xref:System.Drawing.Graphics.FillPie%2A> método é um complemento para o <xref:System.Drawing.Graphics.DrawArc%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91cbb-109">The <xref:System.Drawing.Graphics.FillPie%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawArc%2A> method.</span></span> <span data-ttu-id="91cbb-110">Assim como o <xref:System.Drawing.Graphics.DrawArc%2A> método desenha uma parte da estrutura de tópicos de uma elipse, o <xref:System.Drawing.Graphics.FillPie%2A> método preenche uma parte do interior de uma elipse.</span><span class="sxs-lookup"><span data-stu-id="91cbb-110">Just as the <xref:System.Drawing.Graphics.DrawArc%2A> method draws a portion of the outline of an ellipse, the <xref:System.Drawing.Graphics.FillPie%2A> method fills a portion of the interior of an ellipse.</span></span> <span data-ttu-id="91cbb-111">O exemplo a seguir desenha um arco e preenche a parte correspondente do interior da elipse:</span><span class="sxs-lookup"><span data-stu-id="91cbb-111">The following example draws an arc and fills the corresponding portion of the interior of the ellipse:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 <span data-ttu-id="91cbb-112">A ilustração a seguir mostra o arco e a pizza preenchida.</span><span class="sxs-lookup"><span data-stu-id="91cbb-112">The following illustration shows the arc and the filled pie.</span></span>  
  
 <span data-ttu-id="91cbb-113">![Curvas abertas e fechadas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span><span class="sxs-lookup"><span data-stu-id="91cbb-113">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span></span>  
  
 <span data-ttu-id="91cbb-114">O <xref:System.Drawing.Graphics.FillClosedCurve%2A> método é um complemento para o <xref:System.Drawing.Graphics.DrawClosedCurve%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91cbb-114">The <xref:System.Drawing.Graphics.FillClosedCurve%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method.</span></span> <span data-ttu-id="91cbb-115">Ambos os métodos fecham automaticamente a curva conectando o ponto final ao ponto inicial.</span><span class="sxs-lookup"><span data-stu-id="91cbb-115">Both methods automatically close the curve by connecting the ending point to the starting point.</span></span> <span data-ttu-id="91cbb-116">O exemplo a seguir desenha uma curva que passa por (0, 0), (60, 20) e (40, 50).</span><span class="sxs-lookup"><span data-stu-id="91cbb-116">The following example draws a curve that passes through (0, 0), (60, 20), and (40, 50).</span></span> <span data-ttu-id="91cbb-117">Em seguida, a curva é fechada automaticamente conectando (40, 50) ao ponto inicial (0, 0), e o interior é preenchido com uma cor sólida.</span><span class="sxs-lookup"><span data-stu-id="91cbb-117">Then, the curve is automatically closed by connecting (40, 50) to the starting point (0, 0), and the interior is filled with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <span data-ttu-id="91cbb-118">O <xref:System.Drawing.Graphics.FillPath%2A> método preenche os interiores das partes separadas de um caminho.</span><span class="sxs-lookup"><span data-stu-id="91cbb-118">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the interiors of the separate pieces of a path.</span></span> <span data-ttu-id="91cbb-119">Se uma parte de um demarcador não formar uma curva ou forma fechada, o <xref:System.Drawing.Graphics.FillPath%2A> método fechará automaticamente essa parte do caminho antes de preenchê-lo.</span><span class="sxs-lookup"><span data-stu-id="91cbb-119">If a piece of a path doesn't form a closed curve or shape, the <xref:System.Drawing.Graphics.FillPath%2A> method automatically closes that piece of the path before filling it.</span></span> <span data-ttu-id="91cbb-120">O exemplo a seguir desenha e preenche um demarcador que consiste em um arco, uma spline cardinal, uma cadeia de caracteres e uma pizza:</span><span class="sxs-lookup"><span data-stu-id="91cbb-120">The following example draws and fills a path that consists of an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 <span data-ttu-id="91cbb-121">A ilustração a seguir mostra o demarcador com e sem o preenchimento sólido.</span><span class="sxs-lookup"><span data-stu-id="91cbb-121">The following illustration shows the path with and without the solid fill.</span></span> <span data-ttu-id="91cbb-122">Observe que o texto na cadeia de caracteres é contornado, mas não preenchido, pelo <xref:System.Drawing.Graphics.DrawPath%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91cbb-122">Note that the text in the string is outlined, but not filled, by the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="91cbb-123">É o <xref:System.Drawing.Graphics.FillPath%2A> método que pinta os interiores dos caracteres na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="91cbb-123">It is the <xref:System.Drawing.Graphics.FillPath%2A> method that paints the interiors of the characters in the string.</span></span>  
  
 <span data-ttu-id="91cbb-124">![Cadeia de caracteres em um demarcador](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span><span class="sxs-lookup"><span data-stu-id="91cbb-124">![String in a path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91cbb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91cbb-125">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [<span data-ttu-id="91cbb-126">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="91cbb-126">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="91cbb-127">Como: Criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="91cbb-127">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="91cbb-128">Construindo e desenhando demarcadores</span><span class="sxs-lookup"><span data-stu-id="91cbb-128">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
