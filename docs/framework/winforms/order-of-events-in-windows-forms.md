---
title: Ordem dos eventos em formulários do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 10a6451827a16605ba738cf74b7f684b69adb5dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538459"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="34b1b-102">Ordem dos eventos em formulários do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34b1b-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="34b1b-103">A ordem na qual os eventos são gerados em aplicativos do Windows Forms é de interesse específico para os desenvolvedores preocupados com tratamento de cada um desses eventos sucessivamente.</span><span class="sxs-lookup"><span data-stu-id="34b1b-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="34b1b-104">Quando uma situação exigir tratamento meticuloso de eventos, como quando você estiver redesenhando partes do formulário, será necessário um reconhecimento da ordem exata na qual os eventos são gerados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="34b1b-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="34b1b-105">Este tópico fornece alguns detalhes sobre a ordem dos eventos durante vários estágios importantes no tempo de vida de aplicativos e controles.</span><span class="sxs-lookup"><span data-stu-id="34b1b-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="34b1b-106">Para obter detalhes específicos sobre a ordem de eventos de entrada do mouse, consulte [Eventos de mouse no Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="34b1b-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="34b1b-107">Para obter uma visão geral de eventos no Windows Forms, consulte [Visão geral de eventos](../../../docs/framework/winforms/events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="34b1b-107">For an overview of events in Windows Forms, see [Events Overview](../../../docs/framework/winforms/events-overview-windows-forms.md).</span></span> <span data-ttu-id="34b1b-108">Para obter detalhes sobre a composição de manipuladores de eventos, consulte [Visão geral de manipuladores de eventos](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="34b1b-108">For details about the makeup of event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="34b1b-109">Eventos de inicialização e desligamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="34b1b-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="34b1b-110">O <xref:System.Windows.Forms.Form> e <xref:System.Windows.Forms.Control> classes exponham um conjunto de eventos relacionados ao aplicativo de inicialização e desligamento.</span><span class="sxs-lookup"><span data-stu-id="34b1b-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="34b1b-111">Quando um Aplicativo do Windows Forms é iniciado, os eventos de inicialização do formulário principal são gerados na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="34b1b-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="34b1b-112">Quando um aplicativo é fechado, os eventos de desligamento do formulário principal são gerados na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="34b1b-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="34b1b-113">O <xref:System.Windows.Forms.Application.ApplicationExit> evento o <xref:System.Windows.Forms.Application> classe é gerada após os eventos de desligamento do formulário principal.</span><span class="sxs-lookup"><span data-stu-id="34b1b-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34b1b-114">Visual Basic 2005 inclui eventos de aplicativo adicionais, como <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> e <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34b1b-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="34b1b-115">Eventos de foco e validação</span><span class="sxs-lookup"><span data-stu-id="34b1b-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="34b1b-116">Quando você altera o foco usando o teclado (guia, SHIFT + TAB e assim por diante), chamando o <xref:System.Windows.Forms.Control.Select%2A> ou <xref:System.Windows.Forms.Control.SelectNextControl%2A> métodos, ou definindo o <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade para o formulário atual, eventos de foco do <xref:System.Windows.Forms.Control> classe ocorrem na seguinte ordem :</span><span class="sxs-lookup"><span data-stu-id="34b1b-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="34b1b-117">Quando você altera o foco, usando o mouse ou chamando o <xref:System.Windows.Forms.Control.Focus%2A> método, eventos de foco do <xref:System.Windows.Forms.Control> classe ocorrem na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="34b1b-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="34b1b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34b1b-118">See Also</span></span>  
 [<span data-ttu-id="34b1b-119">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34b1b-119">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
