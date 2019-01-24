---
title: 'Como: Adicionar e remover itens de Menu com o componente do Windows Forms ContextMenu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: ac554f080cdabc7034ca839c3a9086e927429f7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520029"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Como: Adicionar e remover itens de Menu com o componente do Windows Forms ContextMenu
Explica como adicionar e remover itens de menu de atalho no Windows Forms.  
  
 Os formulários do Windows <xref:System.Windows.Forms.ContextMenu> componente fornece um menu de comandos usados com frequência que são relevantes para o objeto selecionado. Você pode adicionar itens ao menu de atalho, adicionando <xref:System.Windows.Forms.MenuItem> objetos para o <xref:System.Windows.Forms.Menu.MenuItems%2A> coleção.  
  
 Você pode remover itens de um menu de atalho permanentemente; No entanto, em tempo de execução pode ser mais apropriado ocultar ou desabilitar os itens em vez disso.  
  
> [!IMPORTANT]
>  Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, os controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Para remover itens de um menu de atalho  
  
1.  Use o <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> ou <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> método o <xref:System.Windows.Forms.Menu.MenuItems%2A> coleção do <xref:System.Windows.Forms.ContextMenu> componente a ser removido de um determinado item do menu.  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     -ou-  
  
2.  Use o `Clear` método da `MenuItems` coleção do <xref:System.Windows.Forms.ContextMenu> componente para remover todos os itens de menu.  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ContextMenu>
- [Componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)
- [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
