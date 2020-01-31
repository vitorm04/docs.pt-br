---
title: Criar borda em torno de um controle usando preenchimento
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
ms.openlocfilehash: 114186ab5784cf892cb01e9fe2648ce22cecc4b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742193"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Como criar uma borda em torno de um controle dos Windows Forms usando preenchimento
O exemplo de código a seguir demonstra como criar uma borda ou um contorno em torno de um controle de <xref:System.Windows.Forms.RichTextBox>. O exemplo define o valor de uma propriedade <xref:System.Windows.Forms.Padding> do controle de <xref:System.Windows.Forms.Panel> como 5 e define a propriedade <xref:System.Windows.Forms.Control.Dock%2A> de um controle filho <xref:System.Windows.Forms.RichTextBox> como <xref:System.Windows.Forms.DockStyle.Fill>. O <xref:System.Windows.Forms.Control.BackColor%2A> do controle de <xref:System.Windows.Forms.Panel> é definido como <xref:System.Drawing.Color.Blue%2A>, que cria uma borda azul em torno do controle de <xref:System.Windows.Forms.RichTextBox>.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Padding>
- [Margem e preenchimento em controles dos Windows Forms](margin-and-padding-in-windows-forms-controls.md)
