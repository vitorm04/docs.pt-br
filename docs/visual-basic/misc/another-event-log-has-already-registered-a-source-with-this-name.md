---
title: Outro log de eventos já registrou uma fonte com esse nome
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: 333c28036e2d1b7514c7370b98ff70a6d195a9dd
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058385"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="d169c-102">Outro log de eventos já registrou uma fonte com esse nome</span><span class="sxs-lookup"><span data-stu-id="d169c-102">Another event log has already registered a source with this name</span></span>

<span data-ttu-id="d169c-103">Foi feita uma tentativa de gravar uma entrada em um log de eventos em que a origem especificada está registrada com outro log de eventos.</span><span class="sxs-lookup"><span data-stu-id="d169c-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="d169c-104">Você deve definir a <xref:System.Diagnostics.EventLog.Source%2A> propriedade da <xref:System.Diagnostics.EventLog> instância do componente antes que o componente grave uma entrada em um log.</span><span class="sxs-lookup"><span data-stu-id="d169c-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="d169c-105">Quando isso acontece, o sistema verifica se a fonte que você especificou está registrada com o log de eventos no qual o componente está gravando e chama, <xref:System.Diagnostics.EventLog.CreateEventSource%2A> se necessário.</span><span class="sxs-lookup"><span data-stu-id="d169c-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d169c-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d169c-106">To correct this error</span></span>  
  
1. <span data-ttu-id="d169c-107">Remova a associação da origem com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> método ou.</span><span class="sxs-lookup"><span data-stu-id="d169c-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2. <span data-ttu-id="d169c-108">Registre a origem com o novo log.</span><span class="sxs-lookup"><span data-stu-id="d169c-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d169c-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="d169c-109">See also</span></span>

- [<span data-ttu-id="d169c-110">Meu. Application. log</span><span class="sxs-lookup"><span data-stu-id="d169c-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
