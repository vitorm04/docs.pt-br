---
title: "Visão geral do controle StatusBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df8e6b8484cf3b35c684445445ddc41adc358698
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="f6c1a-102">Visão geral do controle StatusBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f6c1a-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="f6c1a-103">O <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> controles substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controla; no entanto, o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controles são mantidos para compatibilidade com versões anteriores e o uso futuro, se você Escolha.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="f6c1a-104">O [Controle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) dos Windows Forms é usado em formulários como uma área, normalmente exibido na parte inferior de uma janela, na qual um aplicativo pode exibir diversos tipos de informações de status.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-104">The Windows Forms [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="f6c1a-105"><xref:System.Windows.Forms.StatusBar>controles podem ter painéis de barra de status neles que exibem texto ou ícones para indicar o estado ou uma série de ícones em uma animação que indicam que um processo está funcionando; Por exemplo, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicando que o documento está sendo salvo.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="f6c1a-106">Usando o controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="f6c1a-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="f6c1a-107">O Internet Explorer usa uma barra de status para indicar o URL de uma página quando o mouse passa sobre o hiperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] fornece informações sobre local da página, local de seção e editar modos como sobrescrever e controle de revisão; e [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] usa a barra de status para fornecer informações contextuais, como informá-lo como manipular janelas encaixáveis como encaixadas ou flutuantes.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="f6c1a-108">Você pode exibir uma única mensagem na barra de status, definindo o <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriedade `false` (o padrão) e configuração de <xref:System.Windows.Forms.StatusBar.Text%2A> propriedade da barra de status para o texto que você deseja que apareça na barra de status.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="f6c1a-109">Você pode dividir a barra de status em painéis para exibir mais de um tipo de informação, definindo o <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriedade `true` e usando o <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> método <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c1a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6c1a-110">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="f6c1a-111">Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="f6c1a-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
