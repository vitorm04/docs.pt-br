---
title: "demarcadores de elementos gráficos no GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 022a591a1d646b154c2bd59a2f2ab21b78b9dbda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="1303f-102">demarcadores de elementos gráficos no GDI+</span><span class="sxs-lookup"><span data-stu-id="1303f-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="1303f-103">Os demarcadores são formados combinando linhas, retângulos e curvas simples.</span><span class="sxs-lookup"><span data-stu-id="1303f-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="1303f-104">Lembre-se do [visão geral de elementos gráficos vetoriais](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) que os seguintes blocos de construção básicos provaram para ser mais útil para desenhar imagens:</span><span class="sxs-lookup"><span data-stu-id="1303f-104">Recall from the [Vector Graphics Overview](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="1303f-105">Linhas</span><span class="sxs-lookup"><span data-stu-id="1303f-105">Lines</span></span>  
  
-   <span data-ttu-id="1303f-106">Retângulos</span><span class="sxs-lookup"><span data-stu-id="1303f-106">Rectangles</span></span>  
  
-   <span data-ttu-id="1303f-107">Elipses</span><span class="sxs-lookup"><span data-stu-id="1303f-107">Ellipses</span></span>  
  
-   <span data-ttu-id="1303f-108">Arcos</span><span class="sxs-lookup"><span data-stu-id="1303f-108">Arcs</span></span>  
  
-   <span data-ttu-id="1303f-109">Polígonos</span><span class="sxs-lookup"><span data-stu-id="1303f-109">Polygons</span></span>  
  
-   <span data-ttu-id="1303f-110">Splines cardinais</span><span class="sxs-lookup"><span data-stu-id="1303f-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="1303f-111">Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="1303f-111">Bézier splines</span></span>  
  
 <span data-ttu-id="1303f-112">No GDI+, o <xref:System.Drawing.Drawing2D.GraphicsPath> objeto permite que você colete uma sequência desses blocos de construção em uma única unidade.</span><span class="sxs-lookup"><span data-stu-id="1303f-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="1303f-113">A sequência de inteira de linhas, retângulos, polígonos e curvas, em seguida, pode ser desenhada com uma chamada para o <xref:System.Drawing.Graphics.DrawPath%2A> método o <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="1303f-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="1303f-114">A ilustração a seguir mostra um demarcador criado pela combinação de uma linha, um arco, uma spline de Bézier e uma spline cardinal.</span><span class="sxs-lookup"><span data-stu-id="1303f-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="1303f-115">![Demarcador](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="1303f-115">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="1303f-116">Usando um demarcador</span><span class="sxs-lookup"><span data-stu-id="1303f-116">Using a Path</span></span>  
 <span data-ttu-id="1303f-117">O <xref:System.Drawing.Drawing2D.GraphicsPath> classe fornece os seguintes métodos para criar uma sequência de itens a ser desenhado: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (para splines cardinais), e <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="1303f-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="1303f-118">Cada um desses métodos está sobrecarregado; ou seja, cada método dá suporte a diferentes listas de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1303f-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="1303f-119">Por exemplo, uma variação do <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> método recebe quatro inteiros e outra variação de <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> método recebe dois <xref:System.Drawing.Point> objetos.</span><span class="sxs-lookup"><span data-stu-id="1303f-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="1303f-120">Os métodos para adicionar linhas, retângulos e splines de Bézier em um caminho têm métodos de plural complementar que adicionar vários itens no caminho em uma única chamada: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, e <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="1303f-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="1303f-121">Além disso, o <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> e <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> métodos têm métodos complementar, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> e <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, que adiciona uma curva fechada ou pizza para o caminho.</span><span class="sxs-lookup"><span data-stu-id="1303f-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="1303f-122">Para desenhar um caminho, é necessário um <xref:System.Drawing.Graphics> objeto, um <xref:System.Drawing.Pen> objeto e um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto.</span><span class="sxs-lookup"><span data-stu-id="1303f-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="1303f-123">O <xref:System.Drawing.Graphics> objeto fornece o <xref:System.Drawing.Graphics.DrawPath%2A> método e o <xref:System.Drawing.Pen> objeto armazena atributos, como a largura e a cor da linha usada para renderizar o caminho.</span><span class="sxs-lookup"><span data-stu-id="1303f-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="1303f-124">O <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena a sequência de linhas e curvas que compõem o caminho.</span><span class="sxs-lookup"><span data-stu-id="1303f-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="1303f-125">O <xref:System.Drawing.Pen> objeto e o <xref:System.Drawing.Drawing2D.GraphicsPath> objeto são transmitidos como argumentos para o <xref:System.Drawing.Graphics.DrawPath%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1303f-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="1303f-126">O exemplo a seguir desenha um demarcador que consiste em uma linha, uma elipse e uma spline de Bézier:</span><span class="sxs-lookup"><span data-stu-id="1303f-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="1303f-127">A ilustração a seguir mostra o demarcador.</span><span class="sxs-lookup"><span data-stu-id="1303f-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="1303f-128">![Demarcador](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="1303f-128">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="1303f-129">Além de adicionar linhas, retângulos e curvas a um demarcador, você pode adicionar demarcadores a um demarcador.</span><span class="sxs-lookup"><span data-stu-id="1303f-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="1303f-130">Isso permite combinar os demarcadores existentes para formar demarcadores grandes e complexos.</span><span class="sxs-lookup"><span data-stu-id="1303f-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="1303f-131">Há dois outros itens que você pode adicionar a um demarcador: cadeias de caracteres e pizzas.</span><span class="sxs-lookup"><span data-stu-id="1303f-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="1303f-132">Uma pizza é uma parte do interior de uma elipse.</span><span class="sxs-lookup"><span data-stu-id="1303f-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="1303f-133">O exemplo a seguir cria um demarcador de um arco, uma spline cardinal, uma cadeia de caracteres e uma pizza:</span><span class="sxs-lookup"><span data-stu-id="1303f-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="1303f-134">A ilustração a seguir mostra o demarcador.</span><span class="sxs-lookup"><span data-stu-id="1303f-134">The following illustration shows the path.</span></span> <span data-ttu-id="1303f-135">Observe que um demarcador não precisa estar conectado; o arco, spline cardinal, cadeia de caracteres e pizza são separados.</span><span class="sxs-lookup"><span data-stu-id="1303f-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="1303f-136">![Demarcadores](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="1303f-136">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1303f-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1303f-137">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="1303f-138">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="1303f-138">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="1303f-139">Como Criar Objetos Gráficos para Desenho</span><span class="sxs-lookup"><span data-stu-id="1303f-139">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="1303f-140">Construindo e desenhando demarcadores</span><span class="sxs-lookup"><span data-stu-id="1303f-140">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
