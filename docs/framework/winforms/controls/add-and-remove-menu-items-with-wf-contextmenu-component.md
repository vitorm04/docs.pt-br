---
title: Adicionar e remover itens de menu com componente ContextMenu
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
ms.openlocfilehash: 989ab6d47ec761930a32f542b5fa1136e831f73d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746275"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Como adicionar e remover itens de menu com o componente ContextMenu dos Windows Forms
Explica como adicionar e remover itens de menu de atalho no Windows Forms.  
  
 O componente Windows Forms <xref:System.Windows.Forms.ContextMenu> fornece um menu de comandos usados com frequência que são relevantes para o objeto selecionado. Você pode adicionar itens ao menu de atalho adicionando <xref:System.Windows.Forms.MenuItem> objetos à coleção de <xref:System.Windows.Forms.Menu.MenuItems%2A>.  
  
 Você pode remover itens de um menu de atalho permanentemente; no entanto, em tempo de execução, pode ser mais apropriado ocultar ou desabilitar os itens em vez disso.  
  
> [!IMPORTANT]
> Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade aos controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para a compatibilidade com versões anteriores e o uso futuro, se você escolher.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Para remover itens de um menu de atalho  
  
1. Use o método <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> ou <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> da coleção <xref:System.Windows.Forms.Menu.MenuItems%2A> do componente <xref:System.Windows.Forms.ContextMenu> para remover um item de menu específico.  
  
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
  
2. Use o método `Clear` da coleção `MenuItems` do componente <xref:System.Windows.Forms.ContextMenu> para remover todos os itens do menu.  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ContextMenu>
- [Componente ContextMenu](contextmenu-component-windows-forms.md)
- [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md)
