---
title: Contadores de desempenho de operação
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 46b7d5ff071ebf1e3f790a9b56906d9908028ae9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="operation-performance-counters"></a>Contadores de desempenho de operação
Contadores de desempenho da operação estão localizados sob o `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe). Cada operação tem uma instância individual. Ou seja, se um dado contrato tem operações de 10, 10 instâncias de contador de operação são associadas com esse contrato. As instâncias de objeto são nomeadas usando o seguinte padrão:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Esse contador permite avaliar como a chamada está sendo usada e como a operação está sendo executado.  
  
> [!CAUTION]
>  Há um limite de comprimento do nome de uma instância contador de desempenho. Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.  
  
## <a name="see-also"></a>Consulte também  
 [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
