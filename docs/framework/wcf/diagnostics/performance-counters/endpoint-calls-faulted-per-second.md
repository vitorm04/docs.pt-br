---
title: 'Pontos de extremidade: chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: f1b2997a0f1e16c897fc319d1833313141f5c4bf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082077"
---
# <a name="endpoint-calls-faulted-per-second"></a>Pontos de extremidade: chamadas com falha por segundo
Nome do contador: Chamadas com falha por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas que retornaram falhas para esse ponto de extremidade em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)  
  
 Em aplicativos do Windows Communication Foundation (WCF), métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento. Falhas de SOAP são tipos de mensagem que são incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar sua execução mais robusta ou interativo. Como falhas de SOAP são demonstradas para clientes no formato XML, eles são altamente interoperáveis.  
  
## <a name="see-also"></a>Consulte também  
 [Especificando e lidando com falhas em contratos e serviços](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
