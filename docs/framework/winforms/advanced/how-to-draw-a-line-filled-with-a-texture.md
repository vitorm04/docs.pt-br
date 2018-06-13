---
title: Como desenhar uma linha preenchida com uma textura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 1895c752340d8d764205b5a32b9af0861303841a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522182"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="a0379-102">Como desenhar uma linha preenchida com uma textura</span><span class="sxs-lookup"><span data-stu-id="a0379-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="a0379-103">Em vez de desenhar uma linha com uma cor sólida, você pode desenhar uma linha com uma textura.</span><span class="sxs-lookup"><span data-stu-id="a0379-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="a0379-104">Para desenhar linhas e curvas com uma textura, crie um <xref:System.Drawing.TextureBrush> do objeto e passá-lo <xref:System.Drawing.TextureBrush> o objeto para um <xref:System.Drawing.Pen.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="a0379-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="a0379-105">O bitmap associado ao pincel de textura é usado para organizar lado a lado o plano (modo invisível) e quando a caneta desenha uma linha ou curva, o traço de caneta revela determinados pixels da textura lado a lado.</span><span class="sxs-lookup"><span data-stu-id="a0379-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0379-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0379-106">Example</span></span>  
 <span data-ttu-id="a0379-107">O exemplo a seguir cria um <xref:System.Drawing.Bitmap> objeto do arquivo `Texture1.jpg`.</span><span class="sxs-lookup"><span data-stu-id="a0379-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="a0379-108">Esse bitmap é usado para construir um <xref:System.Drawing.TextureBrush> objeto e o <xref:System.Drawing.TextureBrush> objeto é usado para construir um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="a0379-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="a0379-109">A chamada para <xref:System.Drawing.Graphics.DrawImage%2A> desenha o bitmap com seu canto superior esquerdo em (0, 0).</span><span class="sxs-lookup"><span data-stu-id="a0379-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="a0379-110">A chamada para <xref:System.Drawing.Graphics.DrawEllipse%2A> usa o <xref:System.Drawing.Pen> objeto para desenhar uma elipse texturizada.</span><span class="sxs-lookup"><span data-stu-id="a0379-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="a0379-111">A ilustração a seguir mostra o bitmap e a elipse texturizada.</span><span class="sxs-lookup"><span data-stu-id="a0379-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="a0379-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="a0379-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0379-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a0379-113">Compiling the Code</span></span>  
 <span data-ttu-id="a0379-114">Criar um formulário do Windows e controlar o formulário <xref:System.Windows.Forms.Control.Paint> eventos.</span><span class="sxs-lookup"><span data-stu-id="a0379-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="a0379-115">Cole o código anterior para o <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a0379-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="a0379-116">Substitua `Texture.jpg` por uma imagem válida no sistema.</span><span class="sxs-lookup"><span data-stu-id="a0379-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0379-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0379-117">See Also</span></span>  
 [<span data-ttu-id="a0379-118">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="a0379-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="a0379-119">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0379-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
