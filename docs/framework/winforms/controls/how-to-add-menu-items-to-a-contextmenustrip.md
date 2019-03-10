---
title: 'Como: Adicionar itens de Menu a um ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: a12a201ac73c86bf391d39f47baa47c87bf96095
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716746"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="e5ec4-102">Como: Adicionar itens de Menu a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="e5ec4-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="e5ec4-103">Você pode adicionar apenas um item de menu ou vários itens de cada vez para um <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="e5ec4-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="e5ec4-104">Para adicionar um item de menu único a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="e5ec4-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="e5ec4-105">Use o <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> método para adicionar um item de menu para um <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="e5ec4-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="e5ec4-106">Para adicionar vários itens de menu a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="e5ec4-106">To add several menu items to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="e5ec4-107">Use o <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> método para adicionar vários itens de menu para um <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="e5ec4-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5ec4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5ec4-108">See also</span></span>
- [<span data-ttu-id="e5ec4-109">Controle ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="e5ec4-109">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
