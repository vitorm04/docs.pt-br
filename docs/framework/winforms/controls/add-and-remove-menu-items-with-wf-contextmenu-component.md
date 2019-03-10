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
ms.openlocfilehash: 8b63182bdb37e47a71bee2d22500263cd4889ac9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725058"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="84eba-102">Como: Adicionar e remover itens de Menu com o componente do Windows Forms ContextMenu</span><span class="sxs-lookup"><span data-stu-id="84eba-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="84eba-103">Explica como adicionar e remover itens de menu de atalho no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="84eba-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="84eba-104">Os formulários do Windows <xref:System.Windows.Forms.ContextMenu> componente fornece um menu de comandos usados com frequência que são relevantes para o objeto selecionado.</span><span class="sxs-lookup"><span data-stu-id="84eba-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="84eba-105">Você pode adicionar itens ao menu de atalho, adicionando <xref:System.Windows.Forms.MenuItem> objetos para o <xref:System.Windows.Forms.Menu.MenuItems%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="84eba-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="84eba-106">Você pode remover itens de um menu de atalho permanentemente; No entanto, em tempo de execução pode ser mais apropriado ocultar ou desabilitar os itens em vez disso.</span><span class="sxs-lookup"><span data-stu-id="84eba-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84eba-107">Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, os controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="84eba-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="84eba-108">Para remover itens de um menu de atalho</span><span class="sxs-lookup"><span data-stu-id="84eba-108">To remove items from a shortcut menu</span></span>  
  
1.  <span data-ttu-id="84eba-109">Use o <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> ou <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> método o <xref:System.Windows.Forms.Menu.MenuItems%2A> coleção do <xref:System.Windows.Forms.ContextMenu> componente a ser removido de um determinado item do menu.</span><span class="sxs-lookup"><span data-stu-id="84eba-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="84eba-110">-ou-</span><span class="sxs-lookup"><span data-stu-id="84eba-110">-or-</span></span>  
  
2.  <span data-ttu-id="84eba-111">Use o `Clear` método da `MenuItems` coleção do <xref:System.Windows.Forms.ContextMenu> componente para remover todos os itens de menu.</span><span class="sxs-lookup"><span data-stu-id="84eba-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="84eba-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84eba-112">See also</span></span>
- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="84eba-113">Componente ContextMenu</span><span class="sxs-lookup"><span data-stu-id="84eba-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="84eba-114">Visão geral do componente ContextMenu</span><span class="sxs-lookup"><span data-stu-id="84eba-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
