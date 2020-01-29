---
title: Visão geral do controle MenuStrip
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734472"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="54429-102">Visão geral do controle MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="54429-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="54429-103">Os menus expõem funcionalidades para os usuários, mantendo os comandos que são agrupados por um tema comum.</span><span class="sxs-lookup"><span data-stu-id="54429-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="54429-104">O controle de <xref:System.Windows.Forms.MenuStrip> foi introduzido na versão 2,0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54429-104">The <xref:System.Windows.Forms.MenuStrip> control was introduced in version 2.0 of the .NET Framework.</span></span> <span data-ttu-id="54429-105">Com o controle <xref:System.Windows.Forms.MenuStrip>, você pode facilmente criar menus como aqueles encontrados no Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="54429-105">With the <xref:System.Windows.Forms.MenuStrip> control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="54429-106">O controle <xref:System.Windows.Forms.MenuStrip> dá suporte à interface de vários documentos (MDI) e à mesclagem de menus, a dicas de ferramentas e ao estouro.</span><span class="sxs-lookup"><span data-stu-id="54429-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="54429-107">Você pode melhorar a usabilidade e a legibilidade dos seus menus adicionando teclas de acesso, teclas de atalho, marcas de seleção, imagens e barras separadoras.</span><span class="sxs-lookup"><span data-stu-id="54429-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="54429-108">O controle de <xref:System.Windows.Forms.MenuStrip> substitui e adiciona funcionalidade ao controle de <xref:System.Windows.Forms.MainMenu>; no entanto, o controle de <xref:System.Windows.Forms.MainMenu> é retido para compatibilidade com versões anteriores e uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="54429-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="54429-109">Maneiras de usar o controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="54429-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="54429-110">Use o controle de <xref:System.Windows.Forms.MenuStrip> para:</span><span class="sxs-lookup"><span data-stu-id="54429-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="54429-111">Crie facilmente menus personalizados e comumente usados que dão suporte a recursos avançados de interface do usuário e layout, tais como ordenação e alinhamento de texto e imagem, operações do tipo "arrastar e soltar", MDI, estouro e modos alternativos de acessar os comandos de menu.</span><span class="sxs-lookup"><span data-stu-id="54429-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="54429-112">Suporte à aparência e comportamento típicos do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="54429-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="54429-113">Manipule eventos de forma consistente em todos os contêineres e os itens contidos da mesma forma que você manipula eventos para outros controles.</span><span class="sxs-lookup"><span data-stu-id="54429-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="54429-114">A tabela a seguir mostra algumas propriedades particularmente importantes de <xref:System.Windows.Forms.MenuStrip> e classes associadas.</span><span class="sxs-lookup"><span data-stu-id="54429-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="54429-115">propriedade</span><span class="sxs-lookup"><span data-stu-id="54429-115">Property</span></span>|<span data-ttu-id="54429-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="54429-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="54429-117">Obtém ou define o <xref:System.Windows.Forms.ToolStripMenuItem> usado para exibir uma lista de formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="54429-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="54429-118">Obtém ou define como os menus filho são mescladas com os menus pai em aplicativos MDI.</span><span class="sxs-lookup"><span data-stu-id="54429-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="54429-119">Obtém ou define a posição de um item mesclado dentro de um menu em aplicativos MDI.</span><span class="sxs-lookup"><span data-stu-id="54429-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="54429-120">Obtém ou define um valor que indica se o formulário é um contêiner para formulários MDI filho.</span><span class="sxs-lookup"><span data-stu-id="54429-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="54429-121">Obtém ou define um valor que indica se as dicas de ferramenta são mostradas para o <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="54429-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="54429-122">Obtém ou define um valor que indica se o <xref:System.Windows.Forms.MenuStrip> dá suporte à funcionalidade de estouro.</span><span class="sxs-lookup"><span data-stu-id="54429-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="54429-123">Obtém ou define as teclas de atalho associadas ao <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="54429-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="54429-124">Obtém ou define um valor que indica se as teclas de atalho associadas ao <xref:System.Windows.Forms.ToolStripMenuItem> são exibidas ao lado do <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="54429-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="54429-125">A tabela a seguir mostra as classes importantes do <xref:System.Windows.Forms.MenuStrip> Companion.</span><span class="sxs-lookup"><span data-stu-id="54429-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="54429-126">Classe</span><span class="sxs-lookup"><span data-stu-id="54429-126">Class</span></span>|<span data-ttu-id="54429-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="54429-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="54429-128">Representa uma opção selecionável exibida em um <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="54429-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="54429-129">Representa um menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="54429-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="54429-130">Representa um controle que permite ao usuário selecionar um único item de uma lista que é exibida quando o usuário clica em um <xref:System.Windows.Forms.ToolStripDropDownButton> ou em um item de menu de nível superior.</span><span class="sxs-lookup"><span data-stu-id="54429-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="54429-131">Fornece a funcionalidade básica para controles derivados de <xref:System.Windows.Forms.ToolStripItem> que exibem itens suspensos quando clicados.</span><span class="sxs-lookup"><span data-stu-id="54429-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54429-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="54429-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
