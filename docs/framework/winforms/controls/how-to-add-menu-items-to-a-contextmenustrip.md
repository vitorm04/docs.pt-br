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
ms.openlocfilehash: 7e3480c5a56170ce94d5b5bde0208542c82e7702
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182306"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="fb0c7-102">Como adicionar itens de menu a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="fb0c7-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="fb0c7-103">Você pode adicionar apenas um item de menu ou <xref:System.Windows.Forms.ContextMenuStrip>vários itens de cada vez a um .</span><span class="sxs-lookup"><span data-stu-id="fb0c7-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="fb0c7-104">Para adicionar um único item de menu a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="fb0c7-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="fb0c7-105">Use <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> o método para adicionar um <xref:System.Windows.Forms.ContextMenuStrip>item de menu a um .</span><span class="sxs-lookup"><span data-stu-id="fb0c7-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="fb0c7-106">Para adicionar vários itens de menu a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="fb0c7-106">To add several menu items to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="fb0c7-107">Use <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> o método para adicionar vários <xref:System.Windows.Forms.ContextMenuStrip>itens de menu a um .</span><span class="sxs-lookup"><span data-stu-id="fb0c7-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb0c7-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb0c7-108">See also</span></span>

- [<span data-ttu-id="fb0c7-109">Controle ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="fb0c7-109">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
