---
title: "Visão geral do controle ToolStripPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripPanel
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms], about ToolStripPanel control
ms.assetid: ce54a60c-5eba-4b4c-bd77-cf0748a666cc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d376b5df4fabf63a87be04eca01136e22b3e3f82
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="toolstrippanel-control-overview"></a><span data-ttu-id="b1475-102">Visão geral do controle ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="b1475-102">ToolStripPanel Control Overview</span></span>
<span data-ttu-id="b1475-103">Um <xref:System.Windows.Forms.ToolStripPanel> fornece uma única área de posicionamento e rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="b1475-103">A <xref:System.Windows.Forms.ToolStripPanel> provides a single area for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="b1475-104">Vários <xref:System.Windows.Forms.ToolStrip> controles pilha vertical ou horizontalmente, dependendo do <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> do <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="b1475-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically or horizontally depending on the <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
### <a name="important-toolstrippanel-members"></a><span data-ttu-id="b1475-105">Membros importantes ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="b1475-105">Important ToolStripPanel Members</span></span>  
  
|<span data-ttu-id="b1475-106">Nome</span><span class="sxs-lookup"><span data-stu-id="b1475-106">Name</span></span>|<span data-ttu-id="b1475-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1475-107">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripPanel.Orientation%2A>|<span data-ttu-id="b1475-108">Obtém ou define um valor que indica a orientação horizontal ou vertical do <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="b1475-108">Gets or sets a value indicating the horizontal or vertical orientation of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Renderer%2A>|<span data-ttu-id="b1475-109">Obtém ou define um <xref:System.Windows.Forms.ToolStripRenderer> usado para personalizar a aparência de um <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="b1475-109">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance of a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RenderMode%2A>|<span data-ttu-id="b1475-110">Obtém ou define os estilos de pintura a serem aplicadas para o <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="b1475-110">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RowMargin%2A>|<span data-ttu-id="b1475-111">Obtém ou define o espaçamento, em pixels, entre a <xref:System.Windows.Forms.ToolStripPanelRow> e <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="b1475-111">Gets or sets the spacing, in pixels, between the <xref:System.Windows.Forms.ToolStripPanelRow> and the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Rows%2A>|<span data-ttu-id="b1475-112">Obtém o <xref:System.Windows.Forms.ToolStripPanelRow> neste <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="b1475-112">Gets the <xref:System.Windows.Forms.ToolStripPanelRow> in this <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Join%2A>|<span data-ttu-id="b1475-113">Adiciona um <xref:System.Windows.Forms.ToolStrip> a um <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="b1475-113">Adds a <xref:System.Windows.Forms.ToolStrip> to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1475-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1475-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 [<span data-ttu-id="b1475-115">Exemplo de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b1475-115">ToolStrip Sample</span></span>](http://msdn.microsoft.com/library/b7352439-184a-4a3a-b2ad-07465d3af9ed)
