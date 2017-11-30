---
title: "Visão geral do controle ToolStripProgressBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripProgressBar
helpviewer_keywords:
- toolbars [Windows Forms], progress bars
- progress controls [Windows Forms]
- ToolStripProgressBar control [Windows Forms], about ToolStripProgressBar control
ms.assetid: ec3ab522-5fe4-4b4d-a551-bc19e84f4774
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0db69185df691fe13781e5aed96dedee239d7c9d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="toolstripprogressbar-control-overview"></a><span data-ttu-id="8c909-102">Visão geral do controle ToolStripProgressBar</span><span class="sxs-lookup"><span data-stu-id="8c909-102">ToolStripProgressBar Control Overview</span></span>
<span data-ttu-id="8c909-103">O <xref:System.Windows.Forms.ToolStripProgressBar> combina a funcionalidade de processamento de todas as e rafting <xref:System.Windows.Forms.ToolStrip> controles com sua funcionalidade de controle de processo típico.</span><span class="sxs-lookup"><span data-stu-id="8c909-103">The <xref:System.Windows.Forms.ToolStripProgressBar> combines the rafting and rendering functionality of all <xref:System.Windows.Forms.ToolStrip> controls with its typical process-tracking functionality.</span></span> <span data-ttu-id="8c909-104">Um <xref:System.Windows.Forms.ToolStripProgressBar> mais normalmente é hospedado por <xref:System.Windows.Forms.StatusStrip>e menos frequentemente por um <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="8c909-104">A <xref:System.Windows.Forms.ToolStripProgressBar> is most usually hosted by <xref:System.Windows.Forms.StatusStrip>, and less frequently by a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="8c909-105">Embora <xref:System.Windows.Forms.ToolStripProgressBar> substitui e adiciona a funcionalidade para o controle nas versões anteriores, <xref:System.Windows.Forms.ToolStripProgressBar> é mantido para compatibilidade com versões anteriores e o uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="8c909-105">Although <xref:System.Windows.Forms.ToolStripProgressBar> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolStripProgressBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
### <a name="important-toolstripprogressbar-members"></a><span data-ttu-id="8c909-106">Membros importantes ToolStripProgressBar</span><span class="sxs-lookup"><span data-stu-id="8c909-106">Important ToolStripProgressBar Members</span></span>  
  
|<span data-ttu-id="8c909-107">Nome</span><span class="sxs-lookup"><span data-stu-id="8c909-107">Name</span></span>|<span data-ttu-id="8c909-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c909-108">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripProgressBar.MarqueeAnimationSpeed%2A>|<span data-ttu-id="8c909-109">Obtém ou define um valor que representa o atraso entre cada <xref:System.Windows.Forms.ProgressBarStyle.Marquee> exibir a atualização, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="8c909-109">Gets or sets a value representing the delay between each <xref:System.Windows.Forms.ProgressBarStyle.Marquee> display update, in milliseconds.</span></span>|  
|<xref:System.Windows.Forms.ProgressBar.Maximum%2A>|<span data-ttu-id="8c909-110">Obtém ou define o limite superior do intervalo que está definido para este <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="8c909-110">Gets or sets the upper bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Minimum%2A>|<span data-ttu-id="8c909-111">Obtém ou define o limite inferior do intervalo que está definido para este <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="8c909-111">Gets or sets the lower bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Style%2A>|<span data-ttu-id="8c909-112">Obtém ou define o estilo que o <xref:System.Windows.Forms.ToolStripProgressBar> usa para exibir o progresso de uma operação.</span><span class="sxs-lookup"><span data-stu-id="8c909-112">Gets or sets the style that the <xref:System.Windows.Forms.ToolStripProgressBar> uses to display the progress of an operation.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Value%2A>|<span data-ttu-id="8c909-113">Obtém ou define o valor atual da <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="8c909-113">Gets or sets the current value of the <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.PerformStep%2A>|<span data-ttu-id="8c909-114">Avança a posição atual da barra de progresso até o valor da propriedade <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c909-114">Advances the current position of the progress bar by the amount of the <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c909-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c909-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripProgressBar>
