---
title: 'Práticas recomendadas: intermediárias'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 8b0e0e635c0e790b342115b988905ba29a6b8ad1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296398"
---
# <a name="best-practices-intermediaries"></a>Práticas recomendadas: intermediárias
Deve-se ter cuidado ao lidar com falhas corretamente ao chamar intermediários para certificar-se de canais do lado do serviço em intermediário são fechadas corretamente.  
  
 Considere o cenário a seguir. Um cliente faz uma chamada para um intermediário que, em seguida, chama um serviço de back-end.  O serviço de back-end não define nenhum contrato de falha, portanto, qualquer falha lançada a partir desse serviço será tratada como uma falha não tipada.  O serviço de back-end gerará um <xref:System.ApplicationException> e corretamente, o WCF anulará o canal do lado do serviço. O <xref:System.ApplicationException> , em seguida, revela como um <xref:System.ServiceModel.FaultException> que é gerada para o intermediário. Intermediário gera novamente o <xref:System.ApplicationException>. O WCF interpreta isso como uma falha sem tipo de intermediário e o encaminha para o cliente. Ao receber a falha, intermediário e o cliente falha seus canais do lado do cliente. Canal do lado do serviço do intermediário porém permanece aberta porque o WCF não reconhece que a falha é fatal.  
  
 A prática recomendada neste cenário é detectar se a falha proveniente do serviço é fatal e então intermediário deve falha seu canal do lado do serviço, conforme mostrado no trecho de código a seguir.  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tratamento de erro do WCF](../../../docs/framework/wcf/wcf-error-handling.md)  
 [Especificando e lidando com falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
