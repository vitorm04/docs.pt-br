---
title: 'Como: alinhar um texto desenhado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 5214ef2c69349514f05ba68cc023a7622e119e3a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210445"
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="c68b5-102">Como: alinhar um texto desenhado</span><span class="sxs-lookup"><span data-stu-id="c68b5-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="c68b5-103">Quando você executa um desenho personalizado, você geralmente deseja centralizar o texto desenhado em um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="c68b5-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="c68b5-104">Você pode facilmente alinhar texto desenhado com a <xref:System.Drawing.Graphics.DrawString%2A> ou <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos, criando o objeto de formatação correto e definindo os sinalizadores de formato apropriado.</span><span class="sxs-lookup"><span data-stu-id="c68b5-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="c68b5-105">Para desenhar texto com o GDI+ (DrawString) de centralizado</span><span class="sxs-lookup"><span data-stu-id="c68b5-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1.  <span data-ttu-id="c68b5-106">Use uma <xref:System.Drawing.StringFormat> com os devidos <xref:System.Drawing.Graphics.DrawString%2A> método para especificar o texto centralizado.</span><span class="sxs-lookup"><span data-stu-id="c68b5-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="c68b5-107">Para desenhar texto com GDI (DrawText) de centralizado</span><span class="sxs-lookup"><span data-stu-id="c68b5-107">To draw centered text with GDI (DrawText)</span></span>  
  
1.  <span data-ttu-id="c68b5-108">Use o <xref:System.Windows.Forms.TextFormatFlags> enumeração para quebra automática, bem como verticalmente e horizontalmente centralizar o texto com os devidos <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c68b5-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c68b5-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c68b5-109">Compiling the Code</span></span>  
 <span data-ttu-id="c68b5-110">Os exemplos de código anteriores são projetados para uso com o Windows Forms e exigem <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c68b5-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68b5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c68b5-111">See also</span></span>

- [<span data-ttu-id="c68b5-112">Como: desenhar texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="c68b5-112">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="c68b5-113">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="c68b5-113">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="c68b5-114">Como: construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="c68b5-114">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
