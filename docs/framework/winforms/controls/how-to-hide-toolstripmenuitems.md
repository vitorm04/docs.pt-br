---
title: 'Como: Ocultar ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: 64c0f093063357c1e8db5933c035cc8295ad4f1e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623048"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="5ba94-102">Como: Ocultar ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="5ba94-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="5ba94-103">Ocultando itens de menu é uma maneira de controlar a interface do usuário do seu aplicativo e restringir comandos do usuário.</span><span class="sxs-lookup"><span data-stu-id="5ba94-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="5ba94-104">Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="5ba94-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="5ba94-105">Isso apresenta menos distrações para o usuário.</span><span class="sxs-lookup"><span data-stu-id="5ba94-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="5ba94-106">Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="5ba94-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="5ba94-107">Para ocultar qualquer item de menu de forma programática</span><span class="sxs-lookup"><span data-stu-id="5ba94-107">To hide any menu item programmatically</span></span>  
  
- <span data-ttu-id="5ba94-108">Dentro do método em que você definir as propriedades do item de menu, adicionar código para definir a <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade para `false`.</span><span class="sxs-lookup"><span data-stu-id="5ba94-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5ba94-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ba94-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [<span data-ttu-id="5ba94-110">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="5ba94-110">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="5ba94-111">Como: Desabilitar ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="5ba94-111">How to: Disable ToolStripMenuItems</span></span>](how-to-disable-toolstripmenuitems.md)
