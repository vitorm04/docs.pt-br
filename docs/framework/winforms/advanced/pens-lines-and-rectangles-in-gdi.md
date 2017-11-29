---
title: "Canetas, linhas e retângulos no GDI+"
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
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b72bbaef26e1c61f86e354adc7df7404469ee0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pens-lines-and-rectangles-in-gdi"></a><span data-ttu-id="07b0a-102">Canetas, linhas e retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="07b0a-102">Pens, Lines, and Rectangles in GDI+</span></span>
<span data-ttu-id="07b0a-103">Para desenhar linhas com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] você precisa criar um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="07b0a-103">To draw lines with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you need to create a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="07b0a-104">O <xref:System.Drawing.Graphics> objeto fornece os métodos que possuem o desenho, e o <xref:System.Drawing.Pen> objeto armazena atributos, como cor da linha, largura e estilo.</span><span class="sxs-lookup"><span data-stu-id="07b0a-104">The <xref:System.Drawing.Graphics> object provides the methods that actually do the drawing, and the <xref:System.Drawing.Pen> object stores attributes, such as line color, width, and style.</span></span>  
  
## <a name="drawing-a-line"></a><span data-ttu-id="07b0a-105">Desenhar uma Linha</span><span class="sxs-lookup"><span data-stu-id="07b0a-105">Drawing a Line</span></span>  
 <span data-ttu-id="07b0a-106">Para desenhar uma linha, chame o <xref:System.Drawing.Graphics.DrawLine%2A> método o <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="07b0a-106">To draw a line, call the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="07b0a-107">O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawLine%2A> método.</span><span class="sxs-lookup"><span data-stu-id="07b0a-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="07b0a-108">O exemplo a seguir desenha uma linha do ponto (4, 2) ao ponto (12, 6):</span><span class="sxs-lookup"><span data-stu-id="07b0a-108">The following example draws a line from the point (4, 2) to the point (12, 6):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <span data-ttu-id="07b0a-109"><xref:System.Drawing.Graphics.DrawLine%2A>é um método sobrecarregado a <xref:System.Drawing.Graphics> classe, portanto, há várias maneiras que você pode fornecer argumentos.</span><span class="sxs-lookup"><span data-stu-id="07b0a-109"><xref:System.Drawing.Graphics.DrawLine%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="07b0a-110">Por exemplo, você pode construir dois <xref:System.Drawing.Point> objetos e passe o <xref:System.Drawing.Point> objetos como argumentos para o <xref:System.Drawing.Graphics.DrawLine%2A> método:</span><span class="sxs-lookup"><span data-stu-id="07b0a-110">For example, you can construct two <xref:System.Drawing.Point> objects and pass the <xref:System.Drawing.Point> objects as arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a><span data-ttu-id="07b0a-111">Construir uma Caneta</span><span class="sxs-lookup"><span data-stu-id="07b0a-111">Constructing a Pen</span></span>  
 <span data-ttu-id="07b0a-112">Você pode especificar determinados atributos quando você construir um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="07b0a-112">You can specify certain attributes when you construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="07b0a-113">Por exemplo, um construtor `Pen` permite especificar a cor e a largura.</span><span class="sxs-lookup"><span data-stu-id="07b0a-113">For example, one `Pen` constructor allows you to specify color and width.</span></span> <span data-ttu-id="07b0a-114">O exemplo a seguir desenha uma linha azul de largura 2 de (0, 0) a (60, 30):</span><span class="sxs-lookup"><span data-stu-id="07b0a-114">The following example draws a blue line of width 2 from (0, 0) to (60, 30):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a><span data-ttu-id="07b0a-115">Linhas Tracejadas e Terminações de Linha</span><span class="sxs-lookup"><span data-stu-id="07b0a-115">Dashed Lines and Line Caps</span></span>  
 <span data-ttu-id="07b0a-116">O <xref:System.Drawing.Pen> objeto também expõe as propriedades, como <xref:System.Drawing.Pen.DashStyle%2A>, que você pode usar para especificar os recursos da linha.</span><span class="sxs-lookup"><span data-stu-id="07b0a-116">The <xref:System.Drawing.Pen> object also exposes properties, such as <xref:System.Drawing.Pen.DashStyle%2A>, that you can use to specify features of the line.</span></span> <span data-ttu-id="07b0a-117">O exemplo a seguir desenha uma linha tracejada de (100, 50) a (300, 80):</span><span class="sxs-lookup"><span data-stu-id="07b0a-117">The following example draws a dashed line from (100, 50) to (300, 80):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <span data-ttu-id="07b0a-118">Você pode usar as propriedades do <xref:System.Drawing.Pen> objeto para definir muitos mais atributos da linha.</span><span class="sxs-lookup"><span data-stu-id="07b0a-118">You can use the properties of the <xref:System.Drawing.Pen> object to set many more attributes of the line.</span></span> <span data-ttu-id="07b0a-119">O <xref:System.Drawing.Pen.StartCap%2A> e <xref:System.Drawing.Pen.EndCap%2A> propriedades especificam a aparência das extremidades da linha; as extremidades podem ser simples, quadrado, arredondado, triangular, ou uma forma personalizada.</span><span class="sxs-lookup"><span data-stu-id="07b0a-119">The <xref:System.Drawing.Pen.StartCap%2A> and <xref:System.Drawing.Pen.EndCap%2A> properties specify the appearance of the ends of the line; the ends can be flat, square, rounded, triangular, or a custom shape.</span></span> <span data-ttu-id="07b0a-120">O <xref:System.Drawing.Pen.LineJoin%2A> propriedade permite que você especifique se linhas conectadas são mitre (associadas com os vértices), chanfradas, arredondadas ou recortadas.</span><span class="sxs-lookup"><span data-stu-id="07b0a-120">The <xref:System.Drawing.Pen.LineJoin%2A> property lets you specify whether connected lines are mitered (joined with sharp corners), beveled, rounded, or clipped.</span></span> <span data-ttu-id="07b0a-121">A ilustração a seguir mostra linhas com vários estilos de extremidade e junção.</span><span class="sxs-lookup"><span data-stu-id="07b0a-121">The following illustration shows lines with various cap and join styles.</span></span>  
  
 <span data-ttu-id="07b0a-122">![Lines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span><span class="sxs-lookup"><span data-stu-id="07b0a-122">![Lines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span></span>  
  
## <a name="drawing-a-rectangle"></a><span data-ttu-id="07b0a-123">Desenhar um Retângulo</span><span class="sxs-lookup"><span data-stu-id="07b0a-123">Drawing a Rectangle</span></span>  
 <span data-ttu-id="07b0a-124">Desenhar retângulos com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é semelhante a desenhar linhas.</span><span class="sxs-lookup"><span data-stu-id="07b0a-124">Drawing rectangles with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is similar to drawing lines.</span></span> <span data-ttu-id="07b0a-125">Para desenhar um retângulo, é necessário um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="07b0a-125">To draw a rectangle, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="07b0a-126">O <xref:System.Drawing.Graphics> objeto fornece um <xref:System.Drawing.Graphics.DrawRectangle%2A> método e o <xref:System.Drawing.Pen> objeto armazena atributos, como largura da linha e cor.</span><span class="sxs-lookup"><span data-stu-id="07b0a-126">The <xref:System.Drawing.Graphics> object provides a <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as line width and color.</span></span> <span data-ttu-id="07b0a-127">O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="07b0a-127">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method.</span></span> <span data-ttu-id="07b0a-128">O exemplo a seguir desenha um retângulo com seu canto superior esquerdo em (100, 50), uma largura de 80 e altura de 40:</span><span class="sxs-lookup"><span data-stu-id="07b0a-128">The following example draws a rectangle with its upper-left corner at (100, 50), a width of 80, and a height of 40:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <span data-ttu-id="07b0a-129"><xref:System.Drawing.Graphics.DrawRectangle%2A>é um método sobrecarregado a <xref:System.Drawing.Graphics> classe, portanto, há várias maneiras que você pode fornecer argumentos.</span><span class="sxs-lookup"><span data-stu-id="07b0a-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="07b0a-130">Por exemplo, você pode construir um <xref:System.Drawing.Rectangle> de objeto e passar o <xref:System.Drawing.Rectangle> o objeto para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método como um argumento:</span><span class="sxs-lookup"><span data-stu-id="07b0a-130">For example, you can construct a <xref:System.Drawing.Rectangle> object and pass the <xref:System.Drawing.Rectangle> object to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <span data-ttu-id="07b0a-131">Um <xref:System.Drawing.Rectangle> objeto tem métodos e propriedades para manipular e coleta de informações sobre o retângulo.</span><span class="sxs-lookup"><span data-stu-id="07b0a-131">A <xref:System.Drawing.Rectangle> object has methods and properties for manipulating and gathering information about the rectangle.</span></span> <span data-ttu-id="07b0a-132">Por exemplo, o <xref:System.Drawing.Rectangle.Inflate%2A> e <xref:System.Drawing.Rectangle.Offset%2A> métodos de alterar o tamanho e a posição do retângulo.</span><span class="sxs-lookup"><span data-stu-id="07b0a-132">For example, the <xref:System.Drawing.Rectangle.Inflate%2A> and <xref:System.Drawing.Rectangle.Offset%2A> methods change the size and position of the rectangle.</span></span> <span data-ttu-id="07b0a-133">O <xref:System.Drawing.Rectangle.IntersectsWith%2A> método informa se o retângulo intercepta outra fornecido retângulo e o <xref:System.Drawing.Rectangle.Contains%2A> método informa se um determinado ponto estiver dentro do retângulo.</span><span class="sxs-lookup"><span data-stu-id="07b0a-133">The <xref:System.Drawing.Rectangle.IntersectsWith%2A> method tells you whether the rectangle intersects another given rectangle, and the <xref:System.Drawing.Rectangle.Contains%2A> method tells you whether a given point is inside the rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b0a-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07b0a-134">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Rectangle?displayProperty=nameWithType>  
 [<span data-ttu-id="07b0a-135">Como Criar uma Caneta</span><span class="sxs-lookup"><span data-stu-id="07b0a-135">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="07b0a-136">Como Desenhar uma Linha em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="07b0a-136">How to: Draw a Line on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)  
 [<span data-ttu-id="07b0a-137">Como desenhar uma forma delineada</span><span class="sxs-lookup"><span data-stu-id="07b0a-137">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
