---
title: "Mitigação: chamadas de método EventSource.WriteEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 270f89183bced5d07598b1731f18acf90ec9715a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-eventsourcewriteevent-method-calls"></a><span data-ttu-id="a15ad-102">Mitigação: chamadas de método EventSource.WriteEvent</span><span class="sxs-lookup"><span data-stu-id="a15ad-102">Mitigation: EventSource.WriteEvent Method Calls</span></span>
<span data-ttu-id="a15ad-103">O [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] impõe um contrato entre um método de evento ETW em uma classe derivada de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> e o método <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> da sua classe base.</span><span class="sxs-lookup"><span data-stu-id="a15ad-103">The [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] enforces a contract between an ETW event method in a class that is derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> and  the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method of its base class.</span></span> <span data-ttu-id="a15ad-104">O método de evento ETW deve passar o método <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> para a ID do evento seguida dos mesmos argumentos que foram passados para o método de evento.</span><span class="sxs-lookup"><span data-stu-id="a15ad-104">The ETW event method must pass the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method the event ID followed by the same arguments that were passed to the event method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a15ad-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="a15ad-105">Impact</span></span>  
 <span data-ttu-id="a15ad-106">Um método de evento ETW definido da seguinte maneira interrompe o contrato:</span><span class="sxs-lookup"><span data-stu-id="a15ad-106">An ETW event method defined in the following way breaks the contract:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message, "-");  
}  
```  
  
 <span data-ttu-id="a15ad-107">Quando esse contrato é violado, uma exceção <xref:System.IndexOutOfRangeException> é acionada no tempo de execução se um objeto <xref:System.Diagnostics.Tracing.EventListener> ler dados <xref:System.Diagnostics.Tracing.EventSource> em processo.</span><span class="sxs-lookup"><span data-stu-id="a15ad-107">When this contract is violated, an <xref:System.IndexOutOfRangeException> exception is thrown at run time if an <xref:System.Diagnostics.Tracing.EventListener> object reads <xref:System.Diagnostics.Tracing.EventSource> data in process.</span></span>  
  
 <span data-ttu-id="a15ad-108">A definição desse método de evento ETW deve seguir este padrão:</span><span class="sxs-lookup"><span data-stu-id="a15ad-108">The definition for this ETW event method should follow this pattern:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message);  
}  
```  
  
## <a name="mitigation"></a><span data-ttu-id="a15ad-109">Redução</span><span class="sxs-lookup"><span data-stu-id="a15ad-109">Mitigation</span></span>  
 <span data-ttu-id="a15ad-110">Você deve modificar o código existente de acordo com o padrão necessário.</span><span class="sxs-lookup"><span data-stu-id="a15ad-110">You must modify existing code to conform to the required pattern.</span></span>  
  
 <span data-ttu-id="a15ad-111">Você pode minimizar o volume de código que precisa alterar definindo dois métodos para chamar o método <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A>, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a15ad-111">You can minimize the amount of code that you have to change by defining two methods for calling the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method, as follows:</span></span>  
  
```  
[NonEvent]  
public void Info2(string message)  
{  
   Info2Internal(message, "-");  
}  
  
public void Info2Internal(string message, string prefix)  
{  
   WriteEvent(2, message, prefix);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a15ad-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a15ad-112">See Also</span></span>  
 [<span data-ttu-id="a15ad-113">Alterações no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a15ad-113">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

