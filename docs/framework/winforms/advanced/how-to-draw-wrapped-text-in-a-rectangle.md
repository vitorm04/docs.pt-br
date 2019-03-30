---
title: 'Como: Desenhar texto encapsulado em um retângulo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 35eca2fc0fe40db1b590f4c599baee01c9a9faf3
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654517"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="3b847-102">Como: Desenhar texto encapsulado em um retângulo</span><span class="sxs-lookup"><span data-stu-id="3b847-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="3b847-103">Você pode desenhar texto encapsulado em um retângulo usando o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregada do método da <xref:System.Drawing.Graphics> classe que usa um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3b847-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="3b847-104">Você também usará um <xref:System.Drawing.Brush> e um <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="3b847-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="3b847-105">Você também pode desenhar texto encapsulado em um retângulo usando o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregada do método da <xref:System.Windows.Forms.TextRenderer> que usa um <xref:System.Drawing.Rectangle> e um <xref:System.Windows.Forms.TextFormatFlags> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3b847-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="3b847-106">Você também usará um <xref:System.Drawing.Color> e um <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="3b847-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="3b847-107">A ilustração a seguir mostra a saída de texto desenhada em um retângulo quando você usa o <xref:System.Drawing.Graphics.DrawString%2A> método:</span><span class="sxs-lookup"><span data-stu-id="3b847-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method:</span></span>
  
 ![Captura de tela que mostra a saída ao usar o método DrawString.](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="3b847-109">Para desenhar texto encapsulado em um retângulo com o GDI+</span><span class="sxs-lookup"><span data-stu-id="3b847-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="3b847-110">Use o <xref:System.Drawing.Graphics.DrawString%2A> método, passando o texto que você deseja, sobrecarregado <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> e <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="3b847-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="3b847-111">Para desenhar texto encapsulado em um retângulo com o GDI</span><span class="sxs-lookup"><span data-stu-id="3b847-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="3b847-112">Use o <xref:System.Windows.Forms.TextFormatFlags> valor de enumeração para especificar o texto deve ser empacotado com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregada do método, passando o texto que você deseja, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> e <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="3b847-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b847-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3b847-113">Compiling the Code</span></span>  
 <span data-ttu-id="3b847-114">Os exemplos anteriores requerem:</span><span class="sxs-lookup"><span data-stu-id="3b847-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="3b847-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="3b847-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b847-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b847-116">See also</span></span>
- [<span data-ttu-id="3b847-117">Como: Desenhar texto com GDI</span><span class="sxs-lookup"><span data-stu-id="3b847-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="3b847-118">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="3b847-118">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="3b847-119">Como: Construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="3b847-119">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="3b847-120">Como: Desenhar texto em um local especificado</span><span class="sxs-lookup"><span data-stu-id="3b847-120">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)
