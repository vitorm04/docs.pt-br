---
title: Contadores de desempenho de operação
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 31b0f92ae3477bd3c1de8c348a60e5c64d7c53cc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855685"
---
# <a name="operation-performance-counters"></a>Contadores de desempenho de operação
Os contadores de desempenho de operação são `ServiceModelOperation 4.0.0.0` encontrados no objeto de desempenho ao exibir com o monitor de desempenho (Perfmon. exe). Cada operação tem uma instância individual. Ou seja, se um determinado contrato tiver 10 operações, 10 instâncias do contador de operações serão associadas a esse contrato. As instâncias de objeto são nomeadas usando o seguinte padrão:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Esse contador permite que você meça como a chamada está sendo usada e o quão bem a operação está sendo executada.  
  
> [!CAUTION]
> Há um limite no comprimento do nome de uma instância do contador de desempenho. Quando um nome de instância de contador de Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância por um valor de hash.  
  
## <a name="see-also"></a>Consulte também

- [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
