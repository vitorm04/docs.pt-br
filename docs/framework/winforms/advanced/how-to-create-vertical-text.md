---
title: 'Como: Criar texto Vertical'
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
ms.openlocfilehash: 513d59c61d5195665928f6bb28d1d091b425c103
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573144"
---
# <a name="how-to-create-vertical-text"></a>Como: Criar texto Vertical
Você pode usar um <xref:System.Drawing.StringFormat> objeto para especificar que o texto ser desenhado verticalmente em vez de horizontalmente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir atribui o valor <xref:System.Drawing.StringFormatFlags.DirectionVertical> para o <xref:System.Drawing.StringFormat.FormatFlags%2A> propriedade de um <xref:System.Drawing.StringFormat> objeto. Que <xref:System.Drawing.StringFormat> objeto é passado para o <xref:System.Drawing.Graphics.DrawString%2A> método o <xref:System.Drawing.Graphics> classe. O valor <xref:System.Drawing.StringFormatFlags.DirectionVertical> é um membro do <xref:System.Drawing.StringFormatFlags> enumeração.  
  
 A ilustração a seguir mostra o texto vertical.  
  
 ![Texto de fontes](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e` , que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também
- [Como: Desenhar texto com GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
