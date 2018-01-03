---
title: "Outro log de eventos já registrou uma fonte com esse nome"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="b96f9-102">Outro log de eventos já registrou uma fonte com esse nome</span><span class="sxs-lookup"><span data-stu-id="b96f9-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="b96f9-103">Foi feita uma tentativa para gravar uma entrada para um log de eventos onde a origem especificada é registrada com outro log de eventos.</span><span class="sxs-lookup"><span data-stu-id="b96f9-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="b96f9-104">Você deve definir o <xref:System.Diagnostics.EventLog.Source%2A> propriedade do seu <xref:System.Diagnostics.EventLog> instância do componente antes de seu componente grava uma entrada em um log.</span><span class="sxs-lookup"><span data-stu-id="b96f9-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="b96f9-105">Quando isso acontece, o sistema verifica se a fonte especificada está registrada com o log de eventos para o qual o componente está gravando e chamadas <xref:System.Diagnostics.EventLog.CreateEventSource%2A> se necessário.</span><span class="sxs-lookup"><span data-stu-id="b96f9-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b96f9-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b96f9-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b96f9-107">Remova a associação entre a origem com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> ou <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b96f9-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="b96f9-108">Registre a fonte com o novo log.</span><span class="sxs-lookup"><span data-stu-id="b96f9-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96f9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b96f9-109">See Also</span></span>  
 [<span data-ttu-id="b96f9-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="b96f9-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

