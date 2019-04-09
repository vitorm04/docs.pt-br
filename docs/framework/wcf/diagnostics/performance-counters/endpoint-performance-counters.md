---
title: Contadores de desempenho de ponto de extremidade
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: f07e318e39a68e689ec484b09fa743623cfb51d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158374"
---
# <a name="endpoint-performance-counters"></a>Contadores de desempenho de ponto de extremidade
Contadores de desempenho do ponto de extremidade capturam dados que revela como um ponto de extremidade é aceitar mensagens. Eles podem ser encontrados no `ServiceModelEndpoint 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho. As instâncias são nomeadas usando esse padrão:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Os dados é semelhantes ao que coletados para operações individuais, mas só são agregados entre o ponto de extremidade.  
  
> [!CAUTION]
>  Há um limite no comprimento do nome de uma instância contador de desempenho. Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.  
  
## <a name="see-also"></a>Consulte também

- [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
