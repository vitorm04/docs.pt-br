---
title: 'Como: Usar uma caneta para desenhar retângulos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: 2441687cb36d0780b7fbc935c5cb0edc74bc6ba0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712169"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="59016-102">Como: Usar uma caneta para desenhar retângulos</span><span class="sxs-lookup"><span data-stu-id="59016-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="59016-103">Para desenhar retângulos, é necessário um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="59016-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="59016-104">O <xref:System.Drawing.Graphics> objeto fornece os <xref:System.Drawing.Graphics.DrawRectangle%2A> método e o <xref:System.Drawing.Pen> objeto armazena recursos da linha, como cor e largura.</span><span class="sxs-lookup"><span data-stu-id="59016-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59016-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59016-105">Example</span></span>  
 <span data-ttu-id="59016-106">O exemplo a seguir desenha um retângulo com seu canto superior esquerdo em (10, 10).</span><span class="sxs-lookup"><span data-stu-id="59016-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="59016-107">O retângulo tem uma largura de 100 e uma altura de 50.</span><span class="sxs-lookup"><span data-stu-id="59016-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="59016-108">O segundo argumento passado para o <xref:System.Drawing.Pen.%23ctor%2A> construtor indica que a largura da caneta é 5 pixels.</span><span class="sxs-lookup"><span data-stu-id="59016-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="59016-109">Quando o retângulo é desenhado, a caneta é centralizada no limite do retângulo.</span><span class="sxs-lookup"><span data-stu-id="59016-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="59016-110">Como a largura da caneta é 5, os lados do retângulo são desenhados com 5 pixels de largura, de forma que 1 pixel é desenhado no próprio limite, 2 pixels são desenhados no interior e 2 pixels são desenhados fora.</span><span class="sxs-lookup"><span data-stu-id="59016-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="59016-111">Para obter mais detalhes sobre o alinhamento da caneta, consulte [como: Defina a largura da caneta e o alinhamento](how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="59016-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="59016-112">A ilustração a seguir mostra o retângulo resultante.</span><span class="sxs-lookup"><span data-stu-id="59016-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="59016-113">As linhas pontilhadas mostram onde o retângulo deveria ser desenhado se a largura da caneta tivesse um pixel.</span><span class="sxs-lookup"><span data-stu-id="59016-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="59016-114">A exibição ampliada do canto superior esquerdo do retângulo mostra que as linhas pretas espessas são centralizadas nessas linhas pontilhadas.</span><span class="sxs-lookup"><span data-stu-id="59016-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="59016-115">![Canetas](./media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="59016-115">![Pens](./media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59016-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="59016-116">Compiling the Code</span></span>  
 <span data-ttu-id="59016-117">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="59016-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59016-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59016-118">See also</span></span>
- [<span data-ttu-id="59016-119">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="59016-119">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
