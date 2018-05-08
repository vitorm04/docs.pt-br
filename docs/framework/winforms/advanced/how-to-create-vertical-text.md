---
title: Como criar texto vertical
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 7d66bf147a220bdcdfd32a703d3407817a184a54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-vertical-text"></a>Como criar texto vertical
Você pode usar um <xref:System.Drawing.StringFormat> objeto para especificar que o texto ser desenhada verticalmente em vez de horizontalmente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir atribui o valor <xref:System.Drawing.StringFormatFlags.DirectionVertical> para o <xref:System.Drawing.StringFormat.FormatFlags%2A> propriedade de um <xref:System.Drawing.StringFormat> objeto. Que <xref:System.Drawing.StringFormat> objeto é passado para o <xref:System.Drawing.Graphics.DrawString%2A> método o <xref:System.Drawing.Graphics> classe. O valor <xref:System.Drawing.StringFormatFlags.DirectionVertical> é membro do <xref:System.Drawing.StringFormatFlags> enumeração.  
  
 A ilustração a seguir mostra o texto vertical.  
  
 ![Texto de fontes](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e` , que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Como desenhar texto com o GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
