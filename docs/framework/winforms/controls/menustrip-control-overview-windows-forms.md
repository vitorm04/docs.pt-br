---
title: "Visão geral do controle MenuStrip (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06cd4e812f4acf546dad577a2e1ddc571281ebe3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="0f02b-102">Visão geral do controle MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0f02b-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="0f02b-103">Os menus expõem funcionalidades para os usuários, mantendo os comandos que são agrupados por um tema comum.</span><span class="sxs-lookup"><span data-stu-id="0f02b-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="0f02b-104">O <xref:System.Windows.Forms.MenuStrip> controle há de novo nesta versão do Visual Studio e o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f02b-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="0f02b-105">Com o controle, você pode criar facilmente menus como os encontrados no Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="0f02b-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="0f02b-106">O <xref:System.Windows.Forms.MenuStrip> controle oferece suporte para a interface de documentos múltiplos (MDI) e mesclagem de menus, dicas de ferramenta e estouro.</span><span class="sxs-lookup"><span data-stu-id="0f02b-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="0f02b-107">Você pode melhorar a usabilidade e a legibilidade dos seus menus adicionando teclas de acesso, teclas de atalho, marcas de seleção, imagens e barras separadoras.</span><span class="sxs-lookup"><span data-stu-id="0f02b-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="0f02b-108">O <xref:System.Windows.Forms.MenuStrip> controle substitui e adiciona a funcionalidade para o <xref:System.Windows.Forms.MainMenu> controlar; no entanto, o <xref:System.Windows.Forms.MainMenu> controle é mantido para compatibilidade com versões anteriores e para uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="0f02b-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="0f02b-109">Maneiras de usar o controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="0f02b-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="0f02b-110">Use o <xref:System.Windows.Forms.MenuStrip> controlar para:</span><span class="sxs-lookup"><span data-stu-id="0f02b-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
-   <span data-ttu-id="0f02b-111">Crie facilmente menus personalizados e comumente usados que dão suporte a recursos avançados de interface do usuário e layout, tais como ordenação e alinhamento de texto e imagem, operações do tipo "arrastar e soltar", MDI, estouro e modos alternativos de acessar os comandos de menu.</span><span class="sxs-lookup"><span data-stu-id="0f02b-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
-   <span data-ttu-id="0f02b-112">Suporte à aparência e comportamento típicos do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0f02b-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
-   <span data-ttu-id="0f02b-113">Manipule eventos de forma consistente em todos os contêineres e os itens contidos da mesma forma que você manipula eventos para outros controles.</span><span class="sxs-lookup"><span data-stu-id="0f02b-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="0f02b-114">A tabela a seguir mostra algumas propriedades particularmente importantes de <xref:System.Windows.Forms.MenuStrip> e classes de associados.</span><span class="sxs-lookup"><span data-stu-id="0f02b-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="0f02b-115">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0f02b-115">Property</span></span>|<span data-ttu-id="0f02b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f02b-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="0f02b-117">Obtém ou define o <xref:System.Windows.Forms.ToolStripMenuItem> que é usado para exibir uma lista de formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="0f02b-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="0f02b-118">Obtém ou define como os menus filho são mescladas com os menus pai em aplicativos MDI.</span><span class="sxs-lookup"><span data-stu-id="0f02b-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="0f02b-119">Obtém ou define a posição de um item mesclado dentro de um menu em aplicativos MDI.</span><span class="sxs-lookup"><span data-stu-id="0f02b-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="0f02b-120">Obtém ou define um valor que indica se o formulário é um contêiner para formulários MDI filho.</span><span class="sxs-lookup"><span data-stu-id="0f02b-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="0f02b-121">Obtém ou define um valor que indica se as dicas de ferramenta serão mostradas para o <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="0f02b-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="0f02b-122">Obtém ou define um valor que indica se o <xref:System.Windows.Forms.MenuStrip> dá suporte à funcionalidade de estouro.</span><span class="sxs-lookup"><span data-stu-id="0f02b-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="0f02b-123">Obtém ou define as teclas de atalho associadas ao <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="0f02b-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="0f02b-124">Obtém ou define um valor que indica se as teclas de atalho que estão associados a <xref:System.Windows.Forms.ToolStripMenuItem> são exibidos ao lado de <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="0f02b-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="0f02b-125">A tabela a seguir mostra a importante <xref:System.Windows.Forms.MenuStrip> complementar classes.</span><span class="sxs-lookup"><span data-stu-id="0f02b-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="0f02b-126">Classe</span><span class="sxs-lookup"><span data-stu-id="0f02b-126">Class</span></span>|<span data-ttu-id="0f02b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f02b-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="0f02b-128">Representa uma opção selecionável exibida em uma <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="0f02b-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="0f02b-129">Representa um menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="0f02b-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="0f02b-130">Representa um controle que permite ao usuário selecionar um único item em uma lista que é exibida quando o usuário clica em um <xref:System.Windows.Forms.ToolStripDropDownButton> ou um item de menu de nível superior.</span><span class="sxs-lookup"><span data-stu-id="0f02b-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="0f02b-131">Fornece a funcionalidade básica para controles derivados de <xref:System.Windows.Forms.ToolStripItem> que exibem itens de lista suspensa quando clicado.</span><span class="sxs-lookup"><span data-stu-id="0f02b-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f02b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f02b-132">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
