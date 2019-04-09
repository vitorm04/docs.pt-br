---
title: 'Como: Mover ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 70387a4c43b78f93a46f601eb35b7dca2083b01f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168331"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="76565-102">Como: Mover ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="76565-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="76565-103">Em tempo de design, você pode mover todos os menus de nível superior e seus itens de menu para um local diferente <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="76565-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="76565-104">Você também pode mover itens de menu individuais entre menus de nível superior ou alterar a posição dos itens de menu dentro de um menu.</span><span class="sxs-lookup"><span data-stu-id="76565-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76565-105">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="76565-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="76565-106">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="76565-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="76565-107">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="76565-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="76565-108">Mover um menu de nível superior e seus itens de menu para outro local de nível superior</span><span class="sxs-lookup"><span data-stu-id="76565-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="76565-109">Clique e mantenha pressionado o botão esquerdo do mouse no menu que você deseja mover.</span><span class="sxs-lookup"><span data-stu-id="76565-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="76565-110">Arraste o ponto de inserção para o menu de nível superior que está antes do novo local desejado e solte o botão esquerdo do mouse.</span><span class="sxs-lookup"><span data-stu-id="76565-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="76565-111">O menu selecionado se move para a direita do ponto de inserção.</span><span class="sxs-lookup"><span data-stu-id="76565-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="76565-112">Mover um menu de nível superior e seus itens de menu para outro local suspenso</span><span class="sxs-lookup"><span data-stu-id="76565-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="76565-113">Clique com o botão esquerdo do mouse no menu que você deseja mover e pressione CTRL + X ou clique com o botão direito do mouse no menu e selecione **Recortar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="76565-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="76565-114">No menu de nível superior de destino, clique com o botão esquerdo do mouse no item de menu acima do novo local desejado e pressione CTRL + V, ou clique com o botão direito do mouse no item de menu acima do novo local desejado e selecione **Colar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="76565-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="76565-115">O menu que você recorta é inserido após o item de menu selecionado.</span><span class="sxs-lookup"><span data-stu-id="76565-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="76565-116">Mover um item de menu de dentro de um menu usando o Editor de coleção de itens</span><span class="sxs-lookup"><span data-stu-id="76565-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="76565-117">Clique com o botão direito do mouse no menu que contém o item de menu que você deseja mover.</span><span class="sxs-lookup"><span data-stu-id="76565-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="76565-118">No menu de atalho, escolha **Editar DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="76565-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="76565-119">No **Editor de Coleção de Itens**, clique com o botão esquerdo do mouse no item de menu que você deseja mover.</span><span class="sxs-lookup"><span data-stu-id="76565-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="76565-120">Clique nas teclas de direção para cima e para baixo para mover o item de menu no menu.</span><span class="sxs-lookup"><span data-stu-id="76565-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="76565-121">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="76565-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="76565-122">Mover um item de menu de dentro de um menu usando o teclado</span><span class="sxs-lookup"><span data-stu-id="76565-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="76565-123">Pressione e mantenha a tecla ALT pressionada.</span><span class="sxs-lookup"><span data-stu-id="76565-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="76565-124">Clique e mantenha pressionado o botão esquerdo do mouse no item de menu que você deseja mover.</span><span class="sxs-lookup"><span data-stu-id="76565-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="76565-125">Arraste o item de menu para o novo local e solte o botão esquerdo do mouse.</span><span class="sxs-lookup"><span data-stu-id="76565-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="76565-126">Mover um item de menu para outro menu</span><span class="sxs-lookup"><span data-stu-id="76565-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="76565-127">Clique com o botão esquerdo do mouse no item de menu que você deseja mover e pressione CTRL + X ou clique com o botão direito do mouse no item de menu e escolha **Recortar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="76565-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="76565-128">Clique com o botão esquerdo do mouse no menu que contém o item de menu que você recortou.</span><span class="sxs-lookup"><span data-stu-id="76565-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="76565-129">Clique com o botão esquerdo do mouse no item de menu anterior ao novo local desejado e pressione CTRL + V, ou clique com o botão direito do mouse no item de menu anterior ao novo local desejado e selecione **Colar** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="76565-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="76565-130">O item de menu que você recortou é inserido após o item de menu selecionado.</span><span class="sxs-lookup"><span data-stu-id="76565-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76565-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76565-131">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="76565-132">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="76565-132">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
