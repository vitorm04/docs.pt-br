---
title: 'Como: Adicionar e remover itens de menu com o componente ContextMenu do Windows Forms'
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
ms.openlocfilehash: 5d1862b1fc1398f0f8c2217b51c4efb93db639af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957027"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Como: Adicionar e remover itens de menu com o componente ContextMenu do Windows Forms
Explica como adicionar e remover itens de menu de atalho no Windows Forms.  
  
 O componente <xref:System.Windows.Forms.ContextMenu> Windows Forms fornece um menu de comandos usados com frequência que são relevantes para o objeto selecionado. Você pode adicionar itens ao menu de atalho adicionando <xref:System.Windows.Forms.MenuItem> objetos <xref:System.Windows.Forms.Menu.MenuItems%2A> à coleção.  
  
 Você pode remover itens de um menu de atalho permanentemente; no entanto, em tempo de execução, pode ser mais apropriado ocultar ou desabilitar os itens em vez disso.  
  
> [!IMPORTANT]
> Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.MainMenu> substituam e adicionem funcionalidade aos controles e de versões anteriores, e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher. <xref:System.Windows.Forms.ContextMenuStrip>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Para remover itens de um menu de atalho  
  
1. Use o <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> método <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> <xref:System.Windows.Forms.Menu.MenuItems%2A> ou<xref:System.Windows.Forms.ContextMenu> da coleção do componente para remover um item de menu específico.  
  
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
  
     - ou -  
  
2. Use o `Clear` método `MenuItems` da coleção do <xref:System.Windows.Forms.ContextMenu> componente para remover todos os itens do menu.  
  
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
- [Componente ContextMenu](contextmenu-component-windows-forms.md)
- [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md)
