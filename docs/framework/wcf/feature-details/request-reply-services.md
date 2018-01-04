---
title: "Serviços de resposta por solicitação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e8c01fa3451cbeb335c4771e287566af1c104b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="request-reply-services"></a>Serviços de resposta por solicitação
Serviços de solicitação-resposta são o tipo de padrão de contrato de operação em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Os clientes fazer chamadas para operações de serviço e aguardar uma resposta do serviço. Você pode realizar chamadas para uma operação de serviço ou sincronicamente, onde o cliente bloqueia até ele recebe uma resposta do serviço ou os tempos de chamada ou de forma assíncrona, em que o cliente faz uma chamada para a operação de serviço, continua a trabalhar e recebe o resposta do serviço em outro thread.  
  
 Para criar um contrato de serviço de solicitação-resposta, definir o contrato de serviço e aplicar o <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação, conforme mostrado no código de exemplo a seguir.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Você não precisa definir o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `false` porque esse é o comportamento padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços unidirecionais](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [Serviços duplex](../../../../docs/framework/wcf/feature-details/duplex-services.md)
