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
ms.openlocfilehash: 0e77e4d8eeb9d7a07115b89525ac80074afeb6e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323259"
---
# <a name="how-to-align-drawn-text"></a>Como: alinhar um texto desenhado
Quando você executa um desenho personalizado, você geralmente deseja centralizar o texto desenhado em um formulário ou controle. Você pode facilmente alinhar texto desenhado com a <xref:System.Drawing.Graphics.DrawString%2A> ou <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos, criando o objeto de formatação correto e definindo os sinalizadores de formato apropriado.  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a>Para desenhar texto com o GDI+ (DrawString) de centralizado  
  
1. Use uma <xref:System.Drawing.StringFormat> com os devidos <xref:System.Drawing.Graphics.DrawString%2A> método para especificar o texto centralizado.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a>Para desenhar texto com GDI (DrawText) de centralizado  
  
1. Use o <xref:System.Windows.Forms.TextFormatFlags> enumeração para quebra automática, bem como verticalmente e horizontalmente centralizar o texto com os devidos <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos de código anteriores são projetados para uso com o Windows Forms e exigem <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- [Como: Desenhar texto com GDI](how-to-draw-text-with-gdi.md)
- [Usando fontes e texto](using-fonts-and-text.md)
- [Como: Construir fontes e famílias de fontes](how-to-construct-font-families-and-fonts.md)
