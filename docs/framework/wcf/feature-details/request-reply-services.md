---
title: Serviços de resposta por solicitação
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177808"
---
# <a name="request-reply-services"></a>Serviços de resposta por solicitação
Serviços de solicitação-resposta são o tipo de padrão de contrato de operação no Windows Communication Foundation (WCF). Os clientes fazem chamadas para operações de serviço e aguardam uma resposta do serviço. Você pode realizar chamadas para uma operação de serviço ou forma síncrona, em que o cliente bloqueia até que ele recebe uma resposta do serviço ou os tempos de chamada ou de forma assíncrona, em que o cliente faz uma chamada para a operação de serviço, continua a trabalhar e recebe o resposta do serviço em outro thread.  
  
 Para criar um contrato de serviço de solicitação-resposta, defina seu contrato de serviço e aplique o <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação, conforme mostrado no código de exemplo a seguir.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Você não precisa definir as <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade para `false` porque esse é o comportamento padrão.  
  
## <a name="see-also"></a>Consulte também

- [Serviços unidirecionais](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [Serviços de duplex](../../../../docs/framework/wcf/feature-details/duplex-services.md)
