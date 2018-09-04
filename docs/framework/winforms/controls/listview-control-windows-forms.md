---
title: Controle ListView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- lists
- checked list items [Windows Forms], Windows Forms controls
- user interface [Windows Forms], creating
- lists [Windows Forms], items with icons
- icons [Windows Forms], listing with items
- list views
- ListView control [Windows Forms]
- list controls [Windows Forms], List view
ms.assetid: 9f71cf5c-82da-488a-a04e-ef52c0817187
ms.openlocfilehash: e30f4b21d8b8f1a4c5a168402ce5cc386d932f86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510605"
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="ff279-102">Controle ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ff279-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="ff279-103">O controle `ListView` do Windows Forms exibe uma lista de itens com ícones.</span><span class="sxs-lookup"><span data-stu-id="ff279-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="ff279-104">É possível usar uma exibição de lista para criar uma interface do usuário, como o painel direito do Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="ff279-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff279-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ff279-105">In This Section</span></span>  
 [<span data-ttu-id="ff279-106">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="ff279-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="ff279-107">Descreve esse controle e seus principais recursos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="ff279-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="ff279-108">Como adicionar e remover itens com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-109">Descreve como adicionar ou remover itens de uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="ff279-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="ff279-110">Como adicionar colunas ao controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-111">Descreve como criar colunas para exibir informações sobre cada item de lista.</span><span class="sxs-lookup"><span data-stu-id="ff279-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="ff279-112">Como exibir ícones do controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-113">Descreve como associar uma exibição de lista com uma lista de imagens apropriada para exibir ícones grandes ou pequenos.</span><span class="sxs-lookup"><span data-stu-id="ff279-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="ff279-114">Como exibir subitens em colunas com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-115">Descreve como exibir informações sobre cada item de lista nas colunas.</span><span class="sxs-lookup"><span data-stu-id="ff279-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="ff279-116">Como selecionar um item no controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-117">Descreve como selecionar um item com programação.</span><span class="sxs-lookup"><span data-stu-id="ff279-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="ff279-118">Como agrupar itens em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-119">Descreve como criar grupos para exibição categorizada e como atribuir itens a cada grupo.</span><span class="sxs-lookup"><span data-stu-id="ff279-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="ff279-120">Esse recurso está disponível apenas para [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff279-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="ff279-121">Como habilitar a exibição de bloco em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-122">Descreve como exibir os itens lado a lado, cada um deles composto por um ícone grande e várias linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="ff279-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="ff279-123">Esse recurso está disponível apenas para [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff279-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="ff279-124">Como exibir uma marca de inserção em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="ff279-125">Descreve como implementar os comentários do usuário para operações do tipo "arrastar e soltar" na qual uma marca de inserção indica o local de destino para cada posição do ponteiro do mouse.</span><span class="sxs-lookup"><span data-stu-id="ff279-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="ff279-126">Esse recurso está disponível apenas para [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff279-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="ff279-127">Como adicionar recursos de pesquisa a um controle ListView</span><span class="sxs-lookup"><span data-stu-id="ff279-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="ff279-128">Descreve como localizar um item com programação usando as coordenadas de tela ou pesquisa de texto.</span><span class="sxs-lookup"><span data-stu-id="ff279-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   [<span data-ttu-id="ff279-129">Como habilitar exibição de bloco em um controle ListView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="ff279-129">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>](enable-tile-view-in-a-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="ff279-130">Como adicionar e remover itens com o controle ListView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="ff279-130">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>](add-and-remove-items-with-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="ff279-131">Como adicionar colunas ao controle ListView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="ff279-131">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>](how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="ff279-132">Como agrupar itens em um controle ListView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="ff279-132">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>](how-to-group-items-in-a-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="ff279-133">Instruções passo a passo: criando uma interface no estilo do Explorer com os controles ListView e TreeView usando o Designer</span><span class="sxs-lookup"><span data-stu-id="ff279-133">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>](creating-an-explorer-style-interface-with-the-listview-and-treeview.md)  
  
## <a name="reference"></a><span data-ttu-id="ff279-134">Referência</span><span class="sxs-lookup"><span data-stu-id="ff279-134">Reference</span></span>  
 <span data-ttu-id="ff279-135">Classe <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="ff279-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="ff279-136">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="ff279-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff279-137">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ff279-137">Related Sections</span></span>  
 [<span data-ttu-id="ff279-138">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ff279-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="ff279-139">Descreve como herdar de um item em uma exibição de lista ou um nó em um modo de exibição de árvore para adicionar os campos, métodos ou construtores de que você precisa.</span><span class="sxs-lookup"><span data-stu-id="ff279-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="ff279-140">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="ff279-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="ff279-141">Explica o que é uma lista de imagens e seus principais recursos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="ff279-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="ff279-142">Como criar uma interface do usuário multipainel com o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="ff279-143">Fornece instruções para dispor um Windows Form com vários painéis.</span><span class="sxs-lookup"><span data-stu-id="ff279-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="ff279-144">Recursos do Windows XP e controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-144">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="ff279-145">Explica como aproveitar os recursos específicos do Windows XP que se aplicam ao <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="ff279-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff279-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff279-146">See Also</span></span>  
 [<span data-ttu-id="ff279-147">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff279-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
