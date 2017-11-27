---
title: Eventos com propriedade alterada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7685891e99f1dcb2ca9e515c7dc6d7730ff0b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="property-changed-events"></a><span data-ttu-id="63be5-102">Eventos com propriedade alterada</span><span class="sxs-lookup"><span data-stu-id="63be5-102">Property-Changed Events</span></span>
<span data-ttu-id="63be5-103">Se você quiser que o controle envie notificações quando uma propriedade chamada *PropertyName* mudar, defina um evento chamado *PropertyName* `Changed` e um método chamado `On` *PropertyName* `Changed` que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="63be5-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="63be5-104">A convenção de nomenclatura nos Windows Forms é acrescentar a palavra *Changed* ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="63be5-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="63be5-105">O tipo de delegado do evento associado para eventos de propriedade alterada é <xref:System.EventHandler>, e o tipo de dados de evento é <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="63be5-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="63be5-106">A classe base <xref:System.Windows.Forms.Control> define vários eventos de propriedade alterada, como <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>e outros.</span><span class="sxs-lookup"><span data-stu-id="63be5-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="63be5-107">Para obter informações secundárias sobre eventos, consulte [Eventos](../../../../docs/standard/events/index.md) e [Eventos em controles dos Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="63be5-107">For background information about events, see [Events](../../../../docs/standard/events/index.md) and [Events in Windows Forms Controls](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="63be5-108">Eventos de propriedade alterada são úteis porque permitem que os consumidores de um controle anexem manipuladores de eventos que respondem à alteração.</span><span class="sxs-lookup"><span data-stu-id="63be5-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="63be5-109">Se o seu controle precisa responder a um evento de propriedade alterada que ele emitirá, substitua o método `On` *PropertyName* `Changed` correspondente em vez de associar um delegado ao evento.</span><span class="sxs-lookup"><span data-stu-id="63be5-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="63be5-110">Um controle normalmente responde a um evento de propriedade alterada atualizando outras propriedades ou redesenhando a superfície de alguns ou todos os desenhos.</span><span class="sxs-lookup"><span data-stu-id="63be5-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="63be5-111">A exemplo a seguir mostra como o `FlashTrackBar` controle personalizado responde a alguns dos eventos de propriedade alterada que ele herda de <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="63be5-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="63be5-112">Para um exemplo completo, consulte [Como criar um controle dos Windows Forms que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="63be5-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="63be5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63be5-113">See Also</span></span>  
 [<span data-ttu-id="63be5-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="63be5-114">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="63be5-115">Eventos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63be5-115">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="63be5-116">Propriedades em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63be5-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
