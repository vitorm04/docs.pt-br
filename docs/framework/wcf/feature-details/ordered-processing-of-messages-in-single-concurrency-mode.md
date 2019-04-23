---
title: Processamento ordenado de mensagens em modo de concorrência única
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: 785c2953e57eaf967209b0d9e52ab85a3a99c450
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229713"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="70954-102">Processamento ordenado de mensagens em modo de concorrência única</span><span class="sxs-lookup"><span data-stu-id="70954-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="70954-103">WCF não garante a ordem na qual as mensagens são processadas, a menos que o canal subjacente é sessão.</span><span class="sxs-lookup"><span data-stu-id="70954-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="70954-104">Por exemplo, um serviço WCF que usa MsmqInputChannel, que não é um canal de sessão, falhará processar mensagens na ordem.</span><span class="sxs-lookup"><span data-stu-id="70954-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="70954-105">Há algumas circunstâncias em que um desenvolvedor pode deseja que o comportamento de processamento de pedidos em, mas não quiser usar sessões.</span><span class="sxs-lookup"><span data-stu-id="70954-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="70954-106">Este tópico descreve como configurar esse comportamento quando um serviço está em execução no modo de simultaneidade única.</span><span class="sxs-lookup"><span data-stu-id="70954-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="70954-107">Em ordem de processamento de mensagens</span><span class="sxs-lookup"><span data-stu-id="70954-107">In-order Message Processing</span></span>  
 <span data-ttu-id="70954-108">Um novo atributo chamado <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> foi adicionado para o <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="70954-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="70954-109">Quando <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> é definido como true e <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como <xref:System.ServiceModel.ConcurrencyMode.Single> enviadas para o serviço de mensagens serão processadas na ordem.</span><span class="sxs-lookup"><span data-stu-id="70954-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="70954-110">O trecho de código a seguir ilustra como definir esses atributos.</span><span class="sxs-lookup"><span data-stu-id="70954-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="70954-111">Se <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como qualquer outro valor, um <xref:System.InvalidOperationException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="70954-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70954-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70954-112">See also</span></span>

- [<span data-ttu-id="70954-113">Sessões, instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="70954-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="70954-114">Simultaneidade</span><span class="sxs-lookup"><span data-stu-id="70954-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
