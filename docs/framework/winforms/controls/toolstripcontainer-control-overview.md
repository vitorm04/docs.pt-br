---
title: "Visão geral do controle ToolStripContainer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4abc783961177a55cdb81cefd21ed2d7aefb0620
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="a4f20-102">Visão geral do controle ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="a4f20-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="a4f20-103">Um <xref:System.Windows.Forms.ToolStripContainer> tem painéis em sua esquerda, direita, superior e lados da parte inferior para posicionamento e rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="a4f20-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="a4f20-104">Vários <xref:System.Windows.Forms.ToolStrip> controles de pilha verticalmente se colocá-los na esquerda ou direita <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="a4f20-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="a4f20-105">Horizontalmente pilha se colocá-los na parte superior ou inferior <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="a4f20-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="a4f20-106">Você pode usar o centro <xref:System.Windows.Forms.ToolStripContentPanel> do <xref:System.Windows.Forms.ToolStripContainer> para posicionar tradicionais controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="a4f20-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="a4f20-107">Todos os <xref:System.Windows.Forms.ToolStripContainer> controles são selecionáveis diretamente em tempo de design e pode ser excluídos.</span><span class="sxs-lookup"><span data-stu-id="a4f20-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="a4f20-108">Cada painel de um <xref:System.Windows.Forms.ToolStripContainer> é expansíveis e recolhíveis e redimensiona com os controles que ele contém.</span><span class="sxs-lookup"><span data-stu-id="a4f20-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="a4f20-109">Membros importantes ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="a4f20-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="a4f20-110">Nome</span><span class="sxs-lookup"><span data-stu-id="a4f20-110">Name</span></span>|<span data-ttu-id="a4f20-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4f20-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="a4f20-112">Obtém o painel inferior do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="a4f20-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="a4f20-113">Obtém ou define um valor que indica se o painel inferior do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="a4f20-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="a4f20-114">Obtém o painel esquerdo do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="a4f20-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="a4f20-115">Obtém ou define um valor que indica se o painel esquerdo do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="a4f20-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="a4f20-116">Obtém o painel direito do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="a4f20-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="a4f20-117">Obtém ou define um valor que indica se o painel direito do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="a4f20-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="a4f20-118">Obtém o painel superior do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="a4f20-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="a4f20-119">Obtém ou define um valor que indica se o painel superior do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="a4f20-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4f20-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4f20-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
