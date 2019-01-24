---
title: Contadores de desempenho de operação
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 16608132c6557f8612d42402a2cb2c49fcc29637
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566080"
---
# <a name="operation-performance-counters"></a>Contadores de desempenho de operação
Contadores de desempenho da operação estiverem localizados no `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe). Cada operação tem uma instância individual. Ou seja, se um determinado contrato tem 10 operações, 10 instâncias de contador de operação são associadas esse contrato. As instâncias de objeto são nomeadas usando o seguinte padrão:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Esse contador permite medir como a chamada está sendo usada e como a operação está sendo executado.  
  
> [!CAUTION]
>  Há um limite no comprimento do nome de uma instância contador de desempenho. Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.  
  
## <a name="see-also"></a>Consulte também
- [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
