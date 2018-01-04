---
title: Como alinhar um texto desenhado
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
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6be28641073bf430b1dc51c428228d0fb114d4cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="5ce3e-102">Como alinhar um texto desenhado</span><span class="sxs-lookup"><span data-stu-id="5ce3e-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="5ce3e-103">Quando você executa o desenho personalizado, geralmente convém centralizar o texto desenhado em um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="5ce3e-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="5ce3e-104">Você pode facilmente alinhar texto desenhado com a <xref:System.Drawing.Graphics.DrawString%2A> ou <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos ao criar o objeto de formatação correto e definir os sinalizadores de formato apropriado.</span><span class="sxs-lookup"><span data-stu-id="5ce3e-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="5ce3e-105">Para desenhar texto com o GDI+ (DrawString) centralizado</span><span class="sxs-lookup"><span data-stu-id="5ce3e-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1.  <span data-ttu-id="5ce3e-106">Use um <xref:System.Drawing.StringFormat> com apropriada <xref:System.Drawing.Graphics.DrawString%2A> método para especificar o texto centralizado.</span><span class="sxs-lookup"><span data-stu-id="5ce3e-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="5ce3e-107">Para desenhar texto com GDI (DrawText) centralizado</span><span class="sxs-lookup"><span data-stu-id="5ce3e-107">To draw centered text with GDI (DrawText)</span></span>  
  
1.  <span data-ttu-id="5ce3e-108">Use o <xref:System.Windows.Forms.TextFormatFlags> enumeração para encapsulamento, bem como verticalmente e horizontalmente centralizar o texto com apropriada <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5ce3e-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5ce3e-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5ce3e-109">Compiling the Code</span></span>  
 <span data-ttu-id="5ce3e-110">Os exemplos de código anterior são projetados para uso com o Windows Forms e eles requerem <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="5ce3e-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce3e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ce3e-111">See Also</span></span>  
 [<span data-ttu-id="5ce3e-112">Como desenhar texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="5ce3e-112">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="5ce3e-113">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="5ce3e-113">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="5ce3e-114">Como construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="5ce3e-114">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
