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
ms.openlocfilehash: 5c4e76cda37527d0167b21c0d206749ba6dab4a9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708854"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="dc360-102">Como: Desenhar texto encapsulado em um retângulo</span><span class="sxs-lookup"><span data-stu-id="dc360-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="dc360-103">Você pode desenhar texto encapsulado em um retângulo usando o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregada do método da <xref:System.Drawing.Graphics> classe que usa um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dc360-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="dc360-104">Você também usará um <xref:System.Drawing.Brush> e um <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="dc360-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="dc360-105">Você também pode desenhar texto encapsulado em um retângulo usando o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregada do método da <xref:System.Windows.Forms.TextRenderer> que usa um <xref:System.Drawing.Rectangle> e um <xref:System.Windows.Forms.TextFormatFlags> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dc360-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="dc360-106">Você também usará um <xref:System.Drawing.Color> e um <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="dc360-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="dc360-107">A ilustração a seguir mostra a saída de texto desenhada em um retângulo quando você usa o <xref:System.Drawing.Graphics.DrawString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dc360-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method.</span></span>  
  
 <span data-ttu-id="dc360-108">![Texto de fontes](./media/csfontstext2.png "csfontstext2")</span><span class="sxs-lookup"><span data-stu-id="dc360-108">![Fonts Text](./media/csfontstext2.png "csfontstext2")</span></span>  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="dc360-109">Para desenhar texto encapsulado em um retângulo com o GDI+</span><span class="sxs-lookup"><span data-stu-id="dc360-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="dc360-110">Use o <xref:System.Drawing.Graphics.DrawString%2A> método, passando o texto que você deseja, sobrecarregado <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> e <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="dc360-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="dc360-111">Para desenhar texto encapsulado em um retângulo com o GDI</span><span class="sxs-lookup"><span data-stu-id="dc360-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="dc360-112">Use o <xref:System.Windows.Forms.TextFormatFlags> valor de enumeração para especificar o texto deve ser empacotado com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregada do método, passando o texto que você deseja, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> e <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="dc360-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dc360-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="dc360-113">Compiling the Code</span></span>  
 <span data-ttu-id="dc360-114">Os exemplos anteriores requerem:</span><span class="sxs-lookup"><span data-stu-id="dc360-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="dc360-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="dc360-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc360-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc360-116">See also</span></span>
- [<span data-ttu-id="dc360-117">Como: Desenhar texto com GDI</span><span class="sxs-lookup"><span data-stu-id="dc360-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="dc360-118">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="dc360-118">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="dc360-119">Como: Construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="dc360-119">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="dc360-120">Como: Desenhar texto em um local especificado</span><span class="sxs-lookup"><span data-stu-id="dc360-120">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)
