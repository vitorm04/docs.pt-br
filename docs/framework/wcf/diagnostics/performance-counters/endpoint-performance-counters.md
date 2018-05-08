---
title: Contadores de desempenho de ponto de extremidade
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 9aa741c4482e40a28a2744765114c21973547298
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-performance-counters"></a>Contadores de desempenho de ponto de extremidade
Contadores de desempenho do ponto de extremidade capturar dados revela como um ponto de extremidade é aceitar mensagens. Eles podem ser encontrados no `ServiceModelEndpoint 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho. As instâncias são nomeadas usando esse padrão:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Os dados é semelhantes ao que coletados para as operações individuais, mas só são agregados entre o ponto de extremidade.  
  
> [!CAUTION]
>  Há um limite de comprimento do nome de uma instância contador de desempenho. Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] substitui uma parte do nome da instância com um valor de hash.  
  
## <a name="see-also"></a>Consulte também  
 [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
