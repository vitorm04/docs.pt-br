---
title: "Visão geral do controle divisor (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Splitter
helpviewer_keywords: Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32d8829e7303ce23a22d0a01f2428a889ce4ae0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="e1398-102">Visão geral do controle divisor (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e1398-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="e1398-103">Embora <xref:System.Windows.Forms.SplitContainer> substitua e adicione funcionalidade ao controle <xref:System.Windows.Forms.Splitter> de versões anteriores, <xref:System.Windows.Forms.Splitter> é mantido para compatibilidade com versões anteriores e uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e1398-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="e1398-104">Windows Forms <xref:System.Windows.Forms.Splitter> controles são usados para redimensionar controles encaixados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e1398-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="e1398-105">O <xref:System.Windows.Forms.Splitter> controle é geralmente usado em formulários com controles que têm vários comprimentos de dados para apresentar, como o Windows Explorer, painéis cujos dados contêm informações de larguras diferentes em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="e1398-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="e1398-106">Trabalhando com o controle Splitter</span><span class="sxs-lookup"><span data-stu-id="e1398-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="e1398-107">Quando o usuário aponta o ponteiro do mouse na borda não encaixada de um controle que pode ser redimensionado por um controle splitter, o ponteiro muda de aparência para indicar que o controle pode ser redimensionado.</span><span class="sxs-lookup"><span data-stu-id="e1398-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="e1398-108">Com o controle Splitter, o usuário pode redimensionar o controle encaixado que esteja imediatamente antes dele.</span><span class="sxs-lookup"><span data-stu-id="e1398-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="e1398-109">Portanto, para permitir que o usuário redimensione um controle encaixado em tempo de execução, encaixe o controle a ser redimensionado em uma borda de um contêiner e, em seguida, encaixe um controle Splitter no mesmo lado do contêiner.</span><span class="sxs-lookup"><span data-stu-id="e1398-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1398-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1398-110">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="e1398-111">Como encaixar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1398-111">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="e1398-112">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1398-112">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
