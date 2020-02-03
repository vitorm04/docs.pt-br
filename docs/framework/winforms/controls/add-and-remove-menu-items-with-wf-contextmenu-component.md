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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="1e758-102">Como adicionar e remover itens de menu com o componente ContextMenu dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1e758-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="1e758-103">Explica como adicionar e remover itens de menu de atalho no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1e758-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="1e758-104">O componente Windows Forms <xref:System.Windows.Forms.ContextMenu> fornece um menu de comandos usados com frequência que são relevantes para o objeto selecionado.</span><span class="sxs-lookup"><span data-stu-id="1e758-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="1e758-105">Você pode adicionar itens ao menu de atalho adicionando <xref:System.Windows.Forms.MenuItem> objetos à coleção de <xref:System.Windows.Forms.Menu.MenuItems%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e758-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="1e758-106">Você pode remover itens de um menu de atalho permanentemente; no entanto, em tempo de execução, pode ser mais apropriado ocultar ou desabilitar os itens em vez disso.</span><span class="sxs-lookup"><span data-stu-id="1e758-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1e758-107">Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade aos controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para a compatibilidade com versões anteriores e o uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="1e758-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="1e758-108">Para remover itens de um menu de atalho</span><span class="sxs-lookup"><span data-stu-id="1e758-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="1e758-109">Use o método <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> ou <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> da coleção <xref:System.Windows.Forms.Menu.MenuItems%2A> do componente <xref:System.Windows.Forms.ContextMenu> para remover um item de menu específico.</span><span class="sxs-lookup"><span data-stu-id="1e758-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="1e758-110">-ou-</span><span class="sxs-lookup"><span data-stu-id="1e758-110">-or-</span></span>  
  
2. <span data-ttu-id="1e758-111">Use o método `Clear` da coleção `MenuItems` do componente <xref:System.Windows.Forms.ContextMenu> para remover todos os itens do menu.</span><span class="sxs-lookup"><span data-stu-id="1e758-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1e758-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e758-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="1e758-113">Componente ContextMenu</span><span class="sxs-lookup"><span data-stu-id="1e758-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="1e758-114">Visão geral do componente ContextMenu</span><span class="sxs-lookup"><span data-stu-id="1e758-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
