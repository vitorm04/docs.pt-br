---
title: 'Como: Manipular o evento de abertura ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
ms.openlocfilehash: fe4c8fc3d2446b09add7336fa11670ff9ca8fed2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532104"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Como: Manipular o evento de abertura ContextMenuStrip
Você pode personalizar o comportamento do seu <xref:System.Windows.Forms.ContextMenuStrip> controle manipulando o <xref:System.Windows.Forms.ToolStripDropDown.Opening> eventos.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como manipular o <xref:System.Windows.Forms.ToolStripDropDown.Opening> eventos. O manipulador de eventos adiciona itens dinamicamente para um <xref:System.Windows.Forms.ContextMenuStrip> controle. No exemplo de código completo, consulte [como: Adicionar itens ToolStrip dinamicamente](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Defina as <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> propriedade para `true` para impedir a abertura de menu.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
