---
title: Eventos em controles
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745760"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="f05e4-102">Eventos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f05e4-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="f05e4-103">Um controle de Windows Forms herda mais de 60 eventos de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f05e4-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f05e4-104">Isso inclui o evento <xref:System.Windows.Forms.Control.Paint>, que faz com que um controle seja desenhado, eventos relacionados à exibição de uma janela, como os eventos <xref:System.Windows.Forms.Control.Resize> e <xref:System.Windows.Forms.Control.Layout>, e eventos de teclado e mouse de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="f05e4-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="f05e4-105">Alguns eventos de nível baixo são sintetizados por <xref:System.Windows.Forms.Control> em eventos semânticos, como <xref:System.Windows.Forms.Control.Click> e <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="f05e4-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="f05e4-106">Para obter detalhes sobre os eventos herdados, consulte <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="f05e4-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="f05e4-107">Se o seu controle personalizado precisar substituir a funcionalidade de evento herdado, substitua o método herdado `On`*eventoname* em vez de anexar um delegado.</span><span class="sxs-lookup"><span data-stu-id="f05e4-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="f05e4-108">Se você não estiver familiarizado com o modelo de evento no .NET Framework, consulte [gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="f05e4-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05e4-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f05e4-109">See also</span></span>

- [<span data-ttu-id="f05e4-110">Substituindo o método OnPaint</span><span class="sxs-lookup"><span data-stu-id="f05e4-110">Overriding the OnPaint Method</span></span>](overriding-the-onpaint-method.md)
- [<span data-ttu-id="f05e4-111">Manipulando a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="f05e4-111">Handling User Input</span></span>](handling-user-input.md)
- [<span data-ttu-id="f05e4-112">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="f05e4-112">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="f05e4-113">Eventos</span><span class="sxs-lookup"><span data-stu-id="f05e4-113">Events</span></span>](../../../standard/events/index.md)
