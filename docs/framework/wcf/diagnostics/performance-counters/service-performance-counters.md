---
title: Contadores de desempenho de serviço
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: dc31e05f82f232095f6560c8fdd9bf75c040e2ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773432"
---
# <a name="service-performance-counters"></a>Contadores de desempenho de serviço
Contadores de desempenho serviço medem o comportamento de serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro. Eles podem ser encontrados no `ServiceModelService 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe). As instâncias são nomeadas usando o seguinte padrão:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  Há um limite no comprimento do nome de uma instância contador de desempenho. Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.  
  
## <a name="see-also"></a>Consulte também

- [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
