---
title: Visão geral do controle ToolStripContainer
ms.date: 03/30/2017
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
ms.openlocfilehash: c279316c2a372a1498707b27ec8658813306304b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768326"
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="45a46-102">Visão geral do controle ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="45a46-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="45a46-103">Um <xref:System.Windows.Forms.ToolStripContainer> tem painéis em seu esquerda, direita, superior e lados da parte inferior para posicionamento e reposicionamento <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="45a46-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="45a46-104">Vários <xref:System.Windows.Forms.ToolStrip> controles são empilhados verticalmente ao colocá-los na esquerda ou direita <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="45a46-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="45a46-105">Eles são empilhados horizontalmente se colocá-los na parte superior ou inferior <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="45a46-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="45a46-106">Você pode usar a central <xref:System.Windows.Forms.ToolStripContentPanel> do <xref:System.Windows.Forms.ToolStripContainer> para posicionar controles tradicionais no formulário.</span><span class="sxs-lookup"><span data-stu-id="45a46-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="45a46-107">Uma ou todas as <xref:System.Windows.Forms.ToolStripContainer> controles são selecionáveis diretamente no tempo de design e pode ser excluídos.</span><span class="sxs-lookup"><span data-stu-id="45a46-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="45a46-108">Cada painel de um <xref:System.Windows.Forms.ToolStripContainer> é expansível e recolhível e redimensiona com os controles que ele contém.</span><span class="sxs-lookup"><span data-stu-id="45a46-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="45a46-109">Membros importantes do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="45a46-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="45a46-110">Nome</span><span class="sxs-lookup"><span data-stu-id="45a46-110">Name</span></span>|<span data-ttu-id="45a46-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="45a46-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="45a46-112">Obtém o painel inferior do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="45a46-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="45a46-113">Obtém ou define um valor que indica se o painel inferior do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="45a46-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="45a46-114">Obtém o painel esquerdo do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="45a46-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="45a46-115">Obtém ou define um valor que indica se o painel esquerdo do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="45a46-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="45a46-116">Obtém o painel direito do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="45a46-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="45a46-117">Obtém ou define um valor que indica se o painel direito do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="45a46-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="45a46-118">Obtém o painel superior do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="45a46-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="45a46-119">Obtém ou define um valor que indica se o painel superior do <xref:System.Windows.Forms.ToolStripContainer> está visível.</span><span class="sxs-lookup"><span data-stu-id="45a46-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45a46-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45a46-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- <xref:System.Windows.Forms.ToolStripContentPanel>
