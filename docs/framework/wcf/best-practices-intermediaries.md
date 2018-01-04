---
title: "Práticas recomendadas: intermediárias"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7aecdcecedcee98828b398f9172985d2e09fb9be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-intermediaries"></a>Práticas recomendadas: intermediárias
Deve-se ter cuidado para lidar com falhas corretamente ao chamar intermediários para certificar-se de canais do lado do serviço em intermediária estão fechados corretamente.  
  
 Considere o cenário a seguir. Um cliente faz uma chamada para um intermediário que chama um serviço back-end.  O serviço de back-end não define nenhum contrato de falha, portanto, qualquer falha gerada por esse serviço será tratada como uma falha não digitada.  A serviço de back-end lança um <xref:System.ApplicationException> e WCF corretamente anula o canal do lado do serviço. O <xref:System.ApplicationException> superfícies, em seguida, como um <xref:System.ServiceModel.FaultException> que é gerada para o intermediário. Intermediária gera novamente o <xref:System.ApplicationException>. WCF interpreta como uma falha não digitada do intermediária e a encaminha para o cliente. Ao receber a falha, intermediária e o cliente falha seus canais de cliente. Canal do lado do serviço do intermediário porém permanece aberta porque o WCF não sabe que a falha é fatal.  
  
 É a prática recomendada neste cenário detectar se a falha proveniente do serviço é fatal e então intermediária deve falha seu canal do lado do serviço, conforme mostrado no seguinte trecho de código.  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tratamento de erro do WCF](../../../docs/framework/wcf/wcf-error-handling.md)  
 [Especificando e lidando com falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
