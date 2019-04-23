---
title: Eventos em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 41ad95de7a65dbd0cb3a0d1af8f5c8cb00c1ccdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215879"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="a0ea1-102">Eventos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0ea1-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="a0ea1-103">Um controle dos Windows Forms herda mais de sessenta eventos de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0ea1-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a0ea1-104">Isso inclui o <xref:System.Windows.Forms.Control.Paint> evento, que faz com que um controle a ser desenhado, eventos relacionados ao exibir uma janela, como o <xref:System.Windows.Forms.Control.Resize> e <xref:System.Windows.Forms.Control.Layout> eventos e eventos de mouse e teclado de nível baixo.</span><span class="sxs-lookup"><span data-stu-id="a0ea1-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="a0ea1-105">Alguns eventos de nível inferior são sintetizados por <xref:System.Windows.Forms.Control> sobre eventos de semânticos, como <xref:System.Windows.Forms.Control.Click> e <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="a0ea1-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="a0ea1-106">Para obter detalhes sobre eventos herdados, consulte <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="a0ea1-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="a0ea1-107">Se precisar de seu controle personalizado substituir a funcionalidade de eventos herdados, substituir o herdadas `On` *EventName* método em vez de anexar um delegado.</span><span class="sxs-lookup"><span data-stu-id="a0ea1-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="a0ea1-108">Se você não estiver familiarizado com o modelo de evento no .NET Framework, consulte [gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="a0ea1-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ea1-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0ea1-109">See also</span></span>

- [<span data-ttu-id="a0ea1-110">Substituindo o método OnPaint</span><span class="sxs-lookup"><span data-stu-id="a0ea1-110">Overriding the OnPaint Method</span></span>](overriding-the-onpaint-method.md)
- [<span data-ttu-id="a0ea1-111">Manipulando a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="a0ea1-111">Handling User Input</span></span>](handling-user-input.md)
- [<span data-ttu-id="a0ea1-112">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="a0ea1-112">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="a0ea1-113">Eventos</span><span class="sxs-lookup"><span data-stu-id="a0ea1-113">Events</span></span>](../../../standard/events/index.md)
