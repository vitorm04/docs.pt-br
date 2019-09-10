---
title: Contadores de desempenho de ponto de extremidade
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 72512a15d5b378b1ccb65995441f8f67e251febb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856101"
---
# <a name="endpoint-performance-counters"></a>Contadores de desempenho de ponto de extremidade
Os contadores de desempenho de ponto de extremidade capturam dados que revela como um ponto de extremidade está aceitando mensagens. Eles podem ser encontrados no objeto `ServiceModelEndpoint 4.0.0.0` de desempenho ao exibir com o monitor de desempenho. As instâncias são nomeadas usando esse padrão:  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 Os dados são semelhantes aos coletados para operações individuais, mas são agregados somente no ponto de extremidade.  
  
> [!CAUTION]
> Há um limite no comprimento do nome de uma instância do contador de desempenho. Quando um nome de instância de contador de Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância por um valor de hash.  
  
## <a name="see-also"></a>Consulte também

- [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
