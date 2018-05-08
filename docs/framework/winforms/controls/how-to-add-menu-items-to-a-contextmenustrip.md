---
title: Como adicionar itens de menu a um ContextMenuStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: d044cf92cf7ce6db3425aacf397d6c7b4f111324
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a>Como adicionar itens de menu a um ContextMenuStrip
Você pode adicionar apenas um item de menu ou vários itens de cada vez para um <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a>Para adicionar um item de menu único a um ContextMenuStrip  
  
-   Use o <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> método para adicionar um item de menu para um <xref:System.Windows.Forms.ContextMenuStrip>.  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a>Para adicionar vários itens de menu a um ContextMenuStrip  
  
-   Use o <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> método para adicionar vários itens de menu para um <xref:System.Windows.Forms.ContextMenuStrip>.  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Controle ContextMenuStrip](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
