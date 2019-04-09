---
title: 'Ponto de extremidade: Chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: f425d95868a9ba5bc3c2f2291db2bc414b1918e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122220"
---
# <a name="endpoint-calls-faulted-per-second"></a>Ponto de extremidade: Chamadas com falha por segundo
Nome do contador: Chamadas com falha por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas que retornaram falhas para esse ponto de extremidade em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Em aplicativos do Windows Communication Foundation (WCF), métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento. Falhas de SOAP são tipos de mensagem que são incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar sua execução mais robusta ou interativo. Como falhas de SOAP são demonstradas para clientes no formato XML, eles são altamente interoperáveis.  
  
## <a name="see-also"></a>Consulte também

- [Especificando e lidando com falhas em contratos e serviços](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
