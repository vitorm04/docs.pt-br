---
title: Como habilitar a reorganização de itens ToolStrip em tempo de execução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: 44b52bf997819f090569d08eb395d8af18f61370
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745483"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="fb689-102">Como habilitar a reorganização de itens ToolStrip em tempo de execução no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb689-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="fb689-103">Você pode habilitar o usuário a reorganizar <xref:System.Windows.Forms.ToolStripItem> controles no <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="fb689-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="fb689-104">Para habilitar a reorganização de ToolStripItem em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="fb689-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
- <span data-ttu-id="fb689-105">Defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="fb689-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="fb689-106">Por padrão, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="fb689-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="fb689-107">Em tempo de execução, o usuário mantém pressionada a tecla ALT e o botão esquerdo do mouse para arrastar uma <xref:System.Windows.Forms.ToolStripItem> para um local diferente na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="fb689-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fb689-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb689-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="fb689-109">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="fb689-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="fb689-110">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="fb689-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="fb689-111">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="fb689-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
