---
title: 'Como: Criar uma borda em torno de um Windows Forms usando preenchimento de controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
ms.openlocfilehash: 26d5dd086828df94c1ea0808d2f72723344b0702
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614549"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Como: Criar uma borda em torno de um Windows Forms usando preenchimento de controle
O exemplo de código a seguir demonstra como criar uma borda ou contorno ao redor de um <xref:System.Windows.Forms.RichTextBox> controle. O exemplo define o valor de uma <xref:System.Windows.Forms.Panel> do controle <xref:System.Windows.Forms.Padding> propriedade como 5 e define o <xref:System.Windows.Forms.Control.Dock%2A> propriedade de um filho <xref:System.Windows.Forms.RichTextBox> o controle para <xref:System.Windows.Forms.DockStyle.Fill>. O <xref:System.Windows.Forms.Control.BackColor%2A> do <xref:System.Windows.Forms.Panel> controle é definida como <xref:System.Drawing.Color.Blue%2A>, que cria uma borda azul ao redor de <xref:System.Windows.Forms.RichTextBox> controle.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Padding>
- [Margem e preenchimento em controles dos Windows Forms](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
