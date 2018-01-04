---
title: "Processamento ordenado de mensagens em modo de concorrência única"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c50381c678a84f5602d08342d02dbf44316994c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Processamento ordenado de mensagens em modo de concorrência única
O WCF não garante sobre a ordem na qual as mensagens são processadas, a menos que o canal subjacente é sessão.  Por exemplo, um serviço WCF que usa MsmqInputChannel, que não é um canal de sessão, não processa mensagens na ordem. Há algumas situações em que um desenvolvedor pode deseja que o comportamento de processamento de pedidos em mas não quiser usar sessões. Este tópico descreve como configurar esse comportamento quando um serviço é executado no modo de simultaneidade único.  
  
## <a name="in-order-message-processing"></a>Em ordem de processamento de mensagem  
 Um novo atributo chamado <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> foi adicionado para o <xref:System.ServiceModel.ServiceBehaviorAttribute>. Quando <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> é definido como true e <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como <xref:System.ServiceModel.ConcurrencyMode.Single> mensagens enviadas para o serviço serão processadas na ordem. O trecho de código a seguir ilustra como definir esses atributos.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Se <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como qualquer outro valor, um <xref:System.InvalidOperationException> é gerada.  
  
## <a name="see-also"></a>Consulte também  
 [Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md)
