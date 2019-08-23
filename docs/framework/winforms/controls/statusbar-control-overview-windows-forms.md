---
title: Visão geral do controle StatusBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964430"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="5ad55-102">Visão geral do controle StatusBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5ad55-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="5ad55-103">Os <xref:System.Windows.Forms.StatusStrip> controles <xref:System.Windows.Forms.ToolStripStatusLabel> e <xref:System.Windows.Forms.StatusBar> substituem e adicionam funcionalidade aos <xref:System.Windows.Forms.StatusBarPanel> controles e; no entanto <xref:System.Windows.Forms.StatusBarPanel> , os <xref:System.Windows.Forms.StatusBar> controles e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolha.</span><span class="sxs-lookup"><span data-stu-id="5ad55-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="5ad55-104">O [Controle StatusBar](statusbar-control-windows-forms.md) dos Windows Forms é usado em formulários como uma área, normalmente exibido na parte inferior de uma janela, na qual um aplicativo pode exibir diversos tipos de informações de status.</span><span class="sxs-lookup"><span data-stu-id="5ad55-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="5ad55-105"><xref:System.Windows.Forms.StatusBar>os controles podem ter painéis de barra de status que exibem texto ou ícones para indicar o estado ou uma série de ícones em uma animação que indicam que um processo está funcionando; por exemplo, o Microsoft Word indica que o documento está sendo salvo.</span><span class="sxs-lookup"><span data-stu-id="5ad55-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="5ad55-106">Usando o controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="5ad55-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="5ad55-107">O Internet Explorer usa uma barra de status para indicar a URL de uma página quando o mouse rola sobre o hiperlink; O Microsoft Word fornece informações sobre localização da página, localização da seção e modos de edição, como sobrescrever e controle de revisão; e o Visual Studio usa a barra de status para fornecer informações sensíveis ao contexto, como dizer como manipular janelas encaixáveis como encaixadas ou flutuantes.</span><span class="sxs-lookup"><span data-stu-id="5ad55-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="5ad55-108">Você pode exibir uma única mensagem na barra de status definindo a <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Propriedade como `false` (o padrão) e definindo a <xref:System.Windows.Forms.StatusBar.Text%2A> propriedade da barra de status como o texto que você deseja que apareça na barra de status.</span><span class="sxs-lookup"><span data-stu-id="5ad55-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="5ad55-109">Você pode dividir a barra de status em painéis para exibir mais de um tipo de informação, definindo <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> a propriedade `true` como e usando <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> o método <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>de.</span><span class="sxs-lookup"><span data-stu-id="5ad55-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad55-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ad55-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="5ad55-111">Como: Determine em qual painel no controle StatusBar Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="5ad55-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
