---
title: Como desenhar texto com quebras automáticas de linha em um retângulo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: c753be6a200f166e59e1330c7dbcf1fadc7588a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524967"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="0afed-102">Como desenhar texto com quebras automáticas de linha em um retângulo</span><span class="sxs-lookup"><span data-stu-id="0afed-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="0afed-103">Você pode desenhar texto encapsulado em um retângulo usando o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregado método do <xref:System.Drawing.Graphics> classe que leva um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0afed-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="0afed-104">Você também usará um <xref:System.Drawing.Brush> e um <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="0afed-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="0afed-105">Você também pode desenhar texto encapsulado em um retângulo usando o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> do método sobrecarregado o <xref:System.Windows.Forms.TextRenderer> que leva um <xref:System.Drawing.Rectangle> e um <xref:System.Windows.Forms.TextFormatFlags> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0afed-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="0afed-106">Você também usará um <xref:System.Drawing.Color> e um <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="0afed-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="0afed-107">A ilustração a seguir mostra a saída de texto desenhada no retângulo, quando você usa o <xref:System.Drawing.Graphics.DrawString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0afed-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method.</span></span>  
  
 <span data-ttu-id="0afed-108">![Texto de fontes](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span><span class="sxs-lookup"><span data-stu-id="0afed-108">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span></span>  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="0afed-109">Para desenhar texto encapsulado em um retângulo com o GDI+</span><span class="sxs-lookup"><span data-stu-id="0afed-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="0afed-110">Use o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregado método, passando o texto que você deseja, <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> e <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="0afed-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="0afed-111">Para desenhar texto encapsulado em um retângulo com o GDI</span><span class="sxs-lookup"><span data-stu-id="0afed-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="0afed-112">Use o <xref:System.Windows.Forms.TextFormatFlags> valor de enumeração para especificar o texto deve ser empacotado com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregado método, passando o texto que você deseja, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> e <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="0afed-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0afed-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0afed-113">Compiling the Code</span></span>  
 <span data-ttu-id="0afed-114">Os exemplos anteriores requerem:</span><span class="sxs-lookup"><span data-stu-id="0afed-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="0afed-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0afed-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0afed-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0afed-116">See Also</span></span>  
 [<span data-ttu-id="0afed-117">Como desenhar texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="0afed-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="0afed-118">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="0afed-118">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="0afed-119">Como construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="0afed-119">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [<span data-ttu-id="0afed-120">Como desenhar texto em um local especificado</span><span class="sxs-lookup"><span data-stu-id="0afed-120">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
