---
title: 'Como: desenhar texto em um local especificado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: f7834ea45db8dd6e971defd9c3b2b152ffddf512
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004050"
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="70f4d-102">Como: desenhar texto em um local especificado</span><span class="sxs-lookup"><span data-stu-id="70f4d-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="70f4d-103">Quando você executa um desenho personalizado, você pode desenhar texto em uma única linha horizontal, começando em um ponto especificado.</span><span class="sxs-lookup"><span data-stu-id="70f4d-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="70f4d-104">Você pode desenhar texto dessa maneira, usando o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregada do método da <xref:System.Drawing.Graphics> classe que usa um <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="70f4d-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="70f4d-105">O <xref:System.Drawing.Graphics.DrawString%2A> método também requer um <xref:System.Drawing.Brush> e <xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="70f4d-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="70f4d-106">Você também pode usar o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregada do método da <xref:System.Windows.Forms.TextRenderer> que usa um <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="70f4d-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="70f4d-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> também requer um <xref:System.Drawing.Color> e um <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="70f4d-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="70f4d-108">A ilustração a seguir mostra a saída de texto desenhada em um ponto especificado quando você usa o <xref:System.Drawing.Graphics.DrawString%2A> método sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="70f4d-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 ![Captura de tela que mostra a saída de texto em um ponto especificado.](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="70f4d-110">Para desenhar uma linha de texto com o GDI+</span><span class="sxs-lookup"><span data-stu-id="70f4d-110">To draw a line of text with GDI+</span></span>  
  
1. <span data-ttu-id="70f4d-111">Use o <xref:System.Drawing.Graphics.DrawString%2A> método, passando o texto que você deseja, <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, e <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="70f4d-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="70f4d-112">Para desenhar uma linha de texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="70f4d-112">To draw a line of text with GDI</span></span>  
  
1. <span data-ttu-id="70f4d-113">Use o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método, passando o texto que você deseja, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, e <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="70f4d-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70f4d-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="70f4d-114">Compiling the Code</span></span>  
 <span data-ttu-id="70f4d-115">Os exemplos anteriores requerem:</span><span class="sxs-lookup"><span data-stu-id="70f4d-115">The previous examples require:</span></span>  
  
- <span data-ttu-id="70f4d-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="70f4d-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f4d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70f4d-117">See also</span></span>

- [<span data-ttu-id="70f4d-118">Como: Desenhar texto com GDI</span><span class="sxs-lookup"><span data-stu-id="70f4d-118">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="70f4d-119">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="70f4d-119">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="70f4d-120">Como: Construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="70f4d-120">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="70f4d-121">Como: Desenhar texto encapsulado em um retângulo</span><span class="sxs-lookup"><span data-stu-id="70f4d-121">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)
