---
title: Eventos em controles dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="e5e28-102">Eventos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5e28-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="e5e28-103">Um controle Windows Forms herda mais de sessenta eventos de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5e28-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e5e28-104">Isso inclui o <xref:System.Windows.Forms.Control.Paint> evento, que faz com que um controle a ser desenhada, eventos relacionados ao exibir uma janela, como o <xref:System.Windows.Forms.Control.Resize> e <xref:System.Windows.Forms.Control.Layout> eventos e eventos de mouse e teclado de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="e5e28-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="e5e28-105">Alguns eventos de nível inferior são sintetizados por <xref:System.Windows.Forms.Control> em eventos semânticos como <xref:System.Windows.Forms.Control.Click> e <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="e5e28-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="e5e28-106">Para obter detalhes sobre eventos herdados, consulte <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="e5e28-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="e5e28-107">Se o controle personalizado deve substituir a funcionalidade de eventos herdados, substituir o herdadas `On` *EventName* método em vez de anexar um representante.</span><span class="sxs-lookup"><span data-stu-id="e5e28-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="e5e28-108">Se você não estiver familiarizado com o modelo de evento no .NET Framework, consulte [disparar eventos de um componente](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="e5e28-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e28-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5e28-109">See Also</span></span>  
 [<span data-ttu-id="e5e28-110">Substituindo o método OnPaint</span><span class="sxs-lookup"><span data-stu-id="e5e28-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="e5e28-111">Manipulando a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="e5e28-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="e5e28-112">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="e5e28-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="e5e28-113">Eventos</span><span class="sxs-lookup"><span data-stu-id="e5e28-113">Events</span></span>](../../../../docs/standard/events/index.md)
