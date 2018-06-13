---
title: Serviços de resposta por solicitação
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 8fe1343a4b3590622becf71f1167f4b19dbc67af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490939"
---
# <a name="request-reply-services"></a>Serviços de resposta por solicitação
Serviços de solicitação-resposta são o tipo de padrão de contrato de operação no Windows Communication Foundation (WCF). Os clientes fazer chamadas para operações de serviço e aguardar uma resposta do serviço. Você pode realizar chamadas para uma operação de serviço ou sincronicamente, onde o cliente bloqueia até ele recebe uma resposta do serviço ou os tempos de chamada ou de forma assíncrona, em que o cliente faz uma chamada para a operação de serviço, continua a trabalhar e recebe o resposta do serviço em outro thread.  
  
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
