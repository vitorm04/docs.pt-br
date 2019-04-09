---
title: Canetas, linhas e retângulos no GDI+
ms.date: 03/30/2017
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
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078220"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a><span data-ttu-id="dd5ed-102">Canetas, linhas e retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="dd5ed-102">Pens, Lines, and Rectangles in GDI+</span></span>
<span data-ttu-id="dd5ed-103">Para desenhar linhas com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] você precisa criar um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-103">To draw lines with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you need to create a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="dd5ed-104">O <xref:System.Drawing.Graphics> objeto fornece os métodos que realmente fazem o desenho, e o <xref:System.Drawing.Pen> objeto armazena atributos, como cor da linha, largura e estilo.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-104">The <xref:System.Drawing.Graphics> object provides the methods that actually do the drawing, and the <xref:System.Drawing.Pen> object stores attributes, such as line color, width, and style.</span></span>  
  
## <a name="drawing-a-line"></a><span data-ttu-id="dd5ed-105">Desenhar uma Linha</span><span class="sxs-lookup"><span data-stu-id="dd5ed-105">Drawing a Line</span></span>  
 <span data-ttu-id="dd5ed-106">Para desenhar uma linha, chame o <xref:System.Drawing.Graphics.DrawLine%2A> método da <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-106">To draw a line, call the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="dd5ed-107">O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawLine%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="dd5ed-108">O exemplo a seguir desenha uma linha do ponto (4, 2) ao ponto (12, 6):</span><span class="sxs-lookup"><span data-stu-id="dd5ed-108">The following example draws a line from the point (4, 2) to the point (12, 6):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> <span data-ttu-id="dd5ed-109">é um método sobrecarregado do <xref:System.Drawing.Graphics> de classe, portanto, há várias maneiras que você pode fornecer argumentos.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-109">is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="dd5ed-110">Por exemplo, você pode construir dois <xref:System.Drawing.Point> objetos e passe a <xref:System.Drawing.Point> objetos como argumentos para o <xref:System.Drawing.Graphics.DrawLine%2A> método:</span><span class="sxs-lookup"><span data-stu-id="dd5ed-110">For example, you can construct two <xref:System.Drawing.Point> objects and pass the <xref:System.Drawing.Point> objects as arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a><span data-ttu-id="dd5ed-111">Construir uma Caneta</span><span class="sxs-lookup"><span data-stu-id="dd5ed-111">Constructing a Pen</span></span>  
 <span data-ttu-id="dd5ed-112">Você pode especificar determinados atributos ao construir um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-112">You can specify certain attributes when you construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="dd5ed-113">Por exemplo, um construtor `Pen` permite especificar a cor e a largura.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-113">For example, one `Pen` constructor allows you to specify color and width.</span></span> <span data-ttu-id="dd5ed-114">O exemplo a seguir desenha uma linha azul de largura 2 de (0, 0) a (60, 30):</span><span class="sxs-lookup"><span data-stu-id="dd5ed-114">The following example draws a blue line of width 2 from (0, 0) to (60, 30):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a><span data-ttu-id="dd5ed-115">Linhas Tracejadas e Terminações de Linha</span><span class="sxs-lookup"><span data-stu-id="dd5ed-115">Dashed Lines and Line Caps</span></span>  
 <span data-ttu-id="dd5ed-116">O <xref:System.Drawing.Pen> também expões propriedades, tais como <xref:System.Drawing.Pen.DashStyle%2A>, que você pode usar para especificar os recursos da linha.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-116">The <xref:System.Drawing.Pen> object also exposes properties, such as <xref:System.Drawing.Pen.DashStyle%2A>, that you can use to specify features of the line.</span></span> <span data-ttu-id="dd5ed-117">O exemplo a seguir desenha uma linha tracejada de (100, 50) a (300, 80):</span><span class="sxs-lookup"><span data-stu-id="dd5ed-117">The following example draws a dashed line from (100, 50) to (300, 80):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <span data-ttu-id="dd5ed-118">Você pode usar as propriedades do <xref:System.Drawing.Pen> objeto para definir muitos mais atributos da linha.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-118">You can use the properties of the <xref:System.Drawing.Pen> object to set many more attributes of the line.</span></span> <span data-ttu-id="dd5ed-119">O <xref:System.Drawing.Pen.StartCap%2A> e <xref:System.Drawing.Pen.EndCap%2A> propriedades especificam a aparência das extremidades da linha; as extremidades podem ser simples, quadradas, arredondadas, triangulares ou uma forma personalizada.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-119">The <xref:System.Drawing.Pen.StartCap%2A> and <xref:System.Drawing.Pen.EndCap%2A> properties specify the appearance of the ends of the line; the ends can be flat, square, rounded, triangular, or a custom shape.</span></span> <span data-ttu-id="dd5ed-120">O <xref:System.Drawing.Pen.LineJoin%2A> propriedade permite que você especifique se linhas conectadas estão em Malhete (unidas com cantos), biseladas, arredondadas ou recortadas.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-120">The <xref:System.Drawing.Pen.LineJoin%2A> property lets you specify whether connected lines are mitered (joined with sharp corners), beveled, rounded, or clipped.</span></span> <span data-ttu-id="dd5ed-121">A ilustração a seguir mostra linhas com vários estilos de extremidade e junção.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-121">The following illustration shows lines with various cap and join styles.</span></span>  
  
 <span data-ttu-id="dd5ed-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span><span class="sxs-lookup"><span data-stu-id="dd5ed-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span></span>  
  
## <a name="drawing-a-rectangle"></a><span data-ttu-id="dd5ed-123">Desenhar um Retângulo</span><span class="sxs-lookup"><span data-stu-id="dd5ed-123">Drawing a Rectangle</span></span>  
 <span data-ttu-id="dd5ed-124">Desenhar retângulos com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é semelhante a desenhar linhas.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-124">Drawing rectangles with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is similar to drawing lines.</span></span> <span data-ttu-id="dd5ed-125">Para desenhar um retângulo, você precisa de uma <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-125">To draw a rectangle, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="dd5ed-126">O <xref:System.Drawing.Graphics> objeto fornece uma <xref:System.Drawing.Graphics.DrawRectangle%2A> método e o <xref:System.Drawing.Pen> objeto armazena atributos, como cor e largura da linha.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-126">The <xref:System.Drawing.Graphics> object provides a <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as line width and color.</span></span> <span data-ttu-id="dd5ed-127">O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-127">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method.</span></span> <span data-ttu-id="dd5ed-128">O exemplo a seguir desenha um retângulo com seu canto superior esquerdo em (100, 50), uma largura de 80 e altura de 40:</span><span class="sxs-lookup"><span data-stu-id="dd5ed-128">The following example draws a rectangle with its upper-left corner at (100, 50), a width of 80, and a height of 40:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> <span data-ttu-id="dd5ed-129">é um método sobrecarregado do <xref:System.Drawing.Graphics> de classe, portanto, há várias maneiras que você pode fornecer argumentos.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-129">is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="dd5ed-130">Por exemplo, você pode construir uma <xref:System.Drawing.Rectangle> do objeto e passe a <xref:System.Drawing.Rectangle> do objeto para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método como um argumento:</span><span class="sxs-lookup"><span data-stu-id="dd5ed-130">For example, you can construct a <xref:System.Drawing.Rectangle> object and pass the <xref:System.Drawing.Rectangle> object to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <span data-ttu-id="dd5ed-131">Um <xref:System.Drawing.Rectangle> objeto tem métodos e propriedades para manipular e coletar informações sobre o retângulo.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-131">A <xref:System.Drawing.Rectangle> object has methods and properties for manipulating and gathering information about the rectangle.</span></span> <span data-ttu-id="dd5ed-132">Por exemplo, o <xref:System.Drawing.Rectangle.Inflate%2A> e <xref:System.Drawing.Rectangle.Offset%2A> os métodos de alterar o tamanho e posição do retângulo.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-132">For example, the <xref:System.Drawing.Rectangle.Inflate%2A> and <xref:System.Drawing.Rectangle.Offset%2A> methods change the size and position of the rectangle.</span></span> <span data-ttu-id="dd5ed-133">O <xref:System.Drawing.Rectangle.IntersectsWith%2A> método informa se o retângulo intersecciona outro dado retângulo e o <xref:System.Drawing.Rectangle.Contains%2A> método informa se um determinado ponto está dentro do retângulo.</span><span class="sxs-lookup"><span data-stu-id="dd5ed-133">The <xref:System.Drawing.Rectangle.IntersectsWith%2A> method tells you whether the rectangle intersects another given rectangle, and the <xref:System.Drawing.Rectangle.Contains%2A> method tells you whether a given point is inside the rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5ed-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd5ed-134">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [<span data-ttu-id="dd5ed-135">Como: criar uma caneta</span><span class="sxs-lookup"><span data-stu-id="dd5ed-135">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="dd5ed-136">Como: desenhar uma linha em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="dd5ed-136">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)
- [<span data-ttu-id="dd5ed-137">Como: desenhar uma forma delineada</span><span class="sxs-lookup"><span data-stu-id="dd5ed-137">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
