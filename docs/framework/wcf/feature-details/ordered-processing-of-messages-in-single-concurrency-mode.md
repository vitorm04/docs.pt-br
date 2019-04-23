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
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Processamento ordenado de mensagens em modo de concorrência única
WCF não garante a ordem na qual as mensagens são processadas, a menos que o canal subjacente é sessão.  Por exemplo, um serviço WCF que usa MsmqInputChannel, que não é um canal de sessão, falhará processar mensagens na ordem. Há algumas circunstâncias em que um desenvolvedor pode deseja que o comportamento de processamento de pedidos em, mas não quiser usar sessões. Este tópico descreve como configurar esse comportamento quando um serviço está em execução no modo de simultaneidade única.  
  
## <a name="in-order-message-processing"></a>Em ordem de processamento de mensagens  
 Um novo atributo chamado <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> foi adicionado para o <xref:System.ServiceModel.ServiceBehaviorAttribute>. Quando <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> é definido como true e <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como <xref:System.ServiceModel.ConcurrencyMode.Single> enviadas para o serviço de mensagens serão processadas na ordem. O trecho de código a seguir ilustra como definir esses atributos.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Se <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como qualquer outro valor, um <xref:System.InvalidOperationException> é gerada.  
  
## <a name="see-also"></a>Consulte também

- [Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md)
