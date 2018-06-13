---
title: Elipses e arcos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 6835127d03f984bda8a95cf5b9ca9798122de804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522103"
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="520e1-102">Elipses e arcos no GDI+</span><span class="sxs-lookup"><span data-stu-id="520e1-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="520e1-103">Você pode facilmente desenha elipses e arcos usando o <xref:System.Drawing.Graphics.DrawEllipse%2A> e <xref:System.Drawing.Graphics.DrawArc%2A> métodos de <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="520e1-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="520e1-104">Desenhando uma elipse</span><span class="sxs-lookup"><span data-stu-id="520e1-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="520e1-105">Para desenhar uma elipse, é necessário um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="520e1-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="520e1-106">O <xref:System.Drawing.Graphics> objeto fornece o <xref:System.Drawing.Graphics.DrawEllipse%2A> método e o <xref:System.Drawing.Pen> objeto armazena atributos, como a largura e a cor da linha usada para renderizar a elipse.</span><span class="sxs-lookup"><span data-stu-id="520e1-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="520e1-107">O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método.</span><span class="sxs-lookup"><span data-stu-id="520e1-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="520e1-108">Os argumentos restantes passado para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método especificar o retângulo delimitador para a elipse.</span><span class="sxs-lookup"><span data-stu-id="520e1-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="520e1-109">A ilustração a seguir mostra uma elipse junto a seu retângulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="520e1-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="520e1-110">![Elipses e arcos](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="520e1-110">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="520e1-111">O exemplo a seguir desenha uma elipse; o retângulo delimitador tem uma largura de 80, uma altura de 40 e um canto superior esquerdo de (100, 50):</span><span class="sxs-lookup"><span data-stu-id="520e1-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="520e1-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> é um método sobrecarregado a <xref:System.Drawing.Graphics> classe, portanto, há várias maneiras que você pode fornecer argumentos.</span><span class="sxs-lookup"><span data-stu-id="520e1-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="520e1-113">Por exemplo, você pode construir um <xref:System.Drawing.Rectangle> e passar o <xref:System.Drawing.Rectangle> para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método como um argumento:</span><span class="sxs-lookup"><span data-stu-id="520e1-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="520e1-114">Desenhando um arco</span><span class="sxs-lookup"><span data-stu-id="520e1-114">Drawing an Arc</span></span>  
 <span data-ttu-id="520e1-115">Um arco é uma parte de uma elipse.</span><span class="sxs-lookup"><span data-stu-id="520e1-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="520e1-116">Para desenhar um arco, você deve chamar o <xref:System.Drawing.Graphics.DrawArc%2A> método o <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="520e1-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="520e1-117">Os parâmetros do <xref:System.Drawing.Graphics.DrawArc%2A> método são os mesmos que os parâmetros do <xref:System.Drawing.Graphics.DrawEllipse%2A> método, exceto que <xref:System.Drawing.Graphics.DrawArc%2A> requer um ângulo inicial e ângulo de flecha.</span><span class="sxs-lookup"><span data-stu-id="520e1-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="520e1-118">O exemplo a seguir desenha um arco com um ângulo inicial de 30 graus e um ângulo de flecha de 180 graus:</span><span class="sxs-lookup"><span data-stu-id="520e1-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="520e1-119">A ilustração a seguir mostra o arco, a elipse e o retângulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="520e1-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="520e1-120">![Elipses e arcos](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="520e1-120">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520e1-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="520e1-121">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="520e1-122">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="520e1-122">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="520e1-123">Como Criar Objetos Gráficos para Desenho</span><span class="sxs-lookup"><span data-stu-id="520e1-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="520e1-124">Como criar uma caneta</span><span class="sxs-lookup"><span data-stu-id="520e1-124">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="520e1-125">Como Desenhar uma Forma Delineada</span><span class="sxs-lookup"><span data-stu-id="520e1-125">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
