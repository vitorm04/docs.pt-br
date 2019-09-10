---
title: Contadores de desempenho de serviço
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 4ce0efbeb0a1d6f2409bb976102b8ec8821d5cdc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848989"
---
# <a name="service-performance-counters"></a>Contadores de desempenho de serviço
Os contadores de desempenho de serviço medem o comportamento do serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro. Eles podem ser encontrados no objeto `ServiceModelService 4.0.0.0` de desempenho ao exibir com o monitor de desempenho (Perfmon. exe). As instâncias são nomeadas usando o seguinte padrão:  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> Há um limite no comprimento do nome de uma instância do contador de desempenho. Quando um nome de instância de contador de Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância por um valor de hash.  
  
## <a name="see-also"></a>Consulte também

- [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
