---
title: Como ocultar ToolStripMenuItems usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06a95581e156a7027c8fa0bda6e5fbc4babdb85b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="679a6-102">Como ocultar ToolStripMenuItems usando o designer</span><span class="sxs-lookup"><span data-stu-id="679a6-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="679a6-103">Ocultar itens de menu é uma maneira de controlar a interface do usuário (IU) do seu aplicativo e restringir comandos do usuário.</span><span class="sxs-lookup"><span data-stu-id="679a6-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="679a6-104">Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="679a6-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="679a6-105">Isso apresenta menos distrações para o usuário.</span><span class="sxs-lookup"><span data-stu-id="679a6-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="679a6-106">Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="679a6-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="679a6-107">Para obter mais informações sobre como desabilitar itens de menu, consulte [Como desabilitar ToolStripMenuItems usando o Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="679a6-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="679a6-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="679a6-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="679a6-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="679a6-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="679a6-110">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="679a6-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="679a6-111">Ocultar um menu de nível superior e seus itens de submenu</span><span class="sxs-lookup"><span data-stu-id="679a6-111">To hide a top-level menu and its submenu items</span></span>  
  
1.  <span data-ttu-id="679a6-112">Selecione o item de menu de nível superior e defina seu <xref:System.Windows.Forms.ToolStripItem.Visible%2A> ou <xref:System.Windows.Forms.ToolStripItem.Available%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="679a6-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="679a6-113">Quando você oculta o item de menu de nível superior, todos os itens de menu dentro desse menu também são ocultos.</span><span class="sxs-lookup"><span data-stu-id="679a6-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="679a6-114">Se você clicar em outro lugar que no <xref:System.Windows.Forms.MenuStrip> depois de definir <xref:System.Windows.Forms.ToolStripItem.Visible%2A> para `false`, o item de menu de nível superior inteiro e seus itens de submenu desaparecem do formulário, assim, mostrando o efeito do tempo de execução da ação.</span><span class="sxs-lookup"><span data-stu-id="679a6-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="679a6-115">Para exibir o item de menu de nível superior oculto em tempo de design, clique no <xref:System.Windows.Forms.MenuStrip> no **bandeja de componente**, na **esboço de documento**, ou na parte superior da grade de propriedades.</span><span class="sxs-lookup"><span data-stu-id="679a6-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="679a6-116">Você raramente ocultará um menu inteiro, exceto por menus filho MDI (interface de vários documentos) em um cenário de mesclagem.</span><span class="sxs-lookup"><span data-stu-id="679a6-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="679a6-117">Ocultar um item de submenu</span><span class="sxs-lookup"><span data-stu-id="679a6-117">To hide a submenu item</span></span>  
  
1.  <span data-ttu-id="679a6-118">Selecione o item de submenu e defina seu <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="679a6-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="679a6-119">Quando você oculta um item de submenu, ele permanece visível no formulário no tempo de design para que você pode selecioná-lo facilmente para continuar trabalhando nele.</span><span class="sxs-lookup"><span data-stu-id="679a6-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="679a6-120">Ele será ocultado efetivamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="679a6-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679a6-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="679a6-121">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [<span data-ttu-id="679a6-122">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="679a6-122">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="679a6-123">Como desabilitar ToolStripMenuItems usando o designer</span><span class="sxs-lookup"><span data-stu-id="679a6-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
