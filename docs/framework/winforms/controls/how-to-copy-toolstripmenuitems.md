---
title: 'Como: Copiar ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: d3b1103cda6d4f61b55f6856cd426779a4f39f2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639439"
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="e7425-102">Como: Copiar ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="e7425-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="e7425-103">Em tempo de design, você pode copiar todos os menus de nível superior e seus itens de submenu para um local diferente no <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="e7425-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="e7425-104">Você também pode copiar itens de menu individuais entre menus de nível superior ou alterar a posição dos itens de menu dentro de um menu.</span><span class="sxs-lookup"><span data-stu-id="e7425-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="e7425-105">Copiar um menu de nível superior e seus itens de submenu para outro local de nível superior</span><span class="sxs-lookup"><span data-stu-id="e7425-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="e7425-106">Clique com o botão esquerdo do mouse no menu que você deseja copiar e pressione CTRL + X ou clique com o botão direito do mouse no menu e selecione **Copiar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="e7425-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e7425-107">Clique com o botão esquerdo do mouse no menu superior e posterior ao novo local desejado e pressione CTRL + V ou clique com o botão direito do mouse no item de menu superior e anterior ao novo local desejado e selecione **Colar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="e7425-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="e7425-108">O menu que você copiou é inserido antes do menu de nível superior selecionado.</span><span class="sxs-lookup"><span data-stu-id="e7425-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="e7425-109">Copiar um menu de nível superior e seus itens de submenu para outro local suspenso</span><span class="sxs-lookup"><span data-stu-id="e7425-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="e7425-110">Clique com o botão esquerdo do mouse no menu que você deseja mover e pressione CTRL + C ou clique com o botão direito do mouse no menu e selecione **Copiar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="e7425-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e7425-111">No menu de nível superior de destino, clique com o botão esquerdo do mouse no item de submenu acima do novo local desejado e pressione CTRL + V ou clique com o botão direito do mouse no item de submenu acima do novo local desejado e selecione **Colar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="e7425-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="e7425-112">O menu que você copiou é inserido antes do item de submenu selecionado.</span><span class="sxs-lookup"><span data-stu-id="e7425-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="e7425-113">Copiar um item de submenu para outro menu</span><span class="sxs-lookup"><span data-stu-id="e7425-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="e7425-114">Clique com o botão esquerdo do mouse no submenu que você deseja copiar e pressione CTRL + C ou clique com o botão direito do mouse no item de submenu e escolha **Copiar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="e7425-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e7425-115">Clique com o botão esquerdo do mouse no menu que contém o item de submenu que você recortou.</span><span class="sxs-lookup"><span data-stu-id="e7425-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="e7425-116">Clique com o botão esquerdo do mouse no item de submenu anterior ao novo local desejado e pressione CTRL + V ou clique com o botão direito do mouse no item de submenu anterior ao novo local desejado e selecione **Colar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="e7425-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="e7425-117">O item de submenu que você copiou é inserido antes do item de submenu selecionado.</span><span class="sxs-lookup"><span data-stu-id="e7425-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7425-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7425-118">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="e7425-119">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="e7425-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
