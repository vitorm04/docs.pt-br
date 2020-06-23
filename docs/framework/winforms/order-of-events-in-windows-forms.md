---
title: Ordem dos eventos
description: Aprenda detalhes sobre a ordem de eventos em Windows Forms durante vários estágios importantes no tempo de vida de aplicativos e controles.
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: b16d544d11500b2c684e87a915fc4b8eec071faa
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904332"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="eea35-103">Ordem dos eventos em formulários do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eea35-103">Order of Events in Windows Forms</span></span>
<span data-ttu-id="eea35-104">A ordem na qual os eventos são gerados em aplicativos do Windows Forms é de interesse específico para os desenvolvedores preocupados com tratamento de cada um desses eventos sucessivamente.</span><span class="sxs-lookup"><span data-stu-id="eea35-104">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="eea35-105">Quando uma situação exigir tratamento meticuloso de eventos, como quando você estiver redesenhando partes do formulário, será necessário um reconhecimento da ordem exata na qual os eventos são gerados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="eea35-105">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="eea35-106">Este tópico fornece alguns detalhes sobre a ordem dos eventos durante vários estágios importantes no tempo de vida de aplicativos e controles.</span><span class="sxs-lookup"><span data-stu-id="eea35-106">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="eea35-107">Para obter detalhes específicos sobre a ordem de eventos de entrada do mouse, consulte [Eventos de mouse no Windows Forms](mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="eea35-107">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="eea35-108">Para obter uma visão geral de eventos no Windows Forms, consulte [Visão geral de eventos](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="eea35-108">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="eea35-109">Para obter detalhes sobre a composição de manipuladores de eventos, consulte [Visão geral de manipuladores de eventos](event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="eea35-109">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="eea35-110">Eventos de inicialização e desligamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="eea35-110">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="eea35-111">As <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Control> classes e expõem um conjunto de eventos relacionados à inicialização e ao desligamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eea35-111">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="eea35-112">Quando um Aplicativo do Windows Forms é iniciado, os eventos de inicialização do formulário principal são gerados na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="eea35-112">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="eea35-113">Quando um aplicativo é fechado, os eventos de desligamento do formulário principal são gerados na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="eea35-113">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="eea35-114">O <xref:System.Windows.Forms.Application.ApplicationExit> evento da <xref:System.Windows.Forms.Application> classe é gerado após os eventos de desligamento do formulário principal.</span><span class="sxs-lookup"><span data-stu-id="eea35-114">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eea35-115">Visual Basic 2005 inclui eventos de aplicativo adicionais, como <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> e <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="eea35-115">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="eea35-116">Eventos de foco e validação</span><span class="sxs-lookup"><span data-stu-id="eea35-116">Focus and Validation Events</span></span>  
 <span data-ttu-id="eea35-117">Quando você altera o foco usando o teclado (guia, SHIFT + TAB e assim por diante), chamando os <xref:System.Windows.Forms.Control.Select%2A> <xref:System.Windows.Forms.Control.SelectNextControl%2A> métodos ou, ou definindo a <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade para o formulário atual, os eventos de foco da <xref:System.Windows.Forms.Control> classe ocorrem na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="eea35-117">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="eea35-118">Quando você altera o foco usando o mouse ou chamando o <xref:System.Windows.Forms.Control.Focus%2A> método, os eventos de foco da <xref:System.Windows.Forms.Control> classe ocorrem na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="eea35-118">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="eea35-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="eea35-119">See also</span></span>

- [<span data-ttu-id="eea35-120">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eea35-120">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
