---
title: 'Pontos de extremidade: chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: ead4b074748307f30d16557c3359f730880595da
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163534"
---
# <a name="endpoint-calls-faulted-per-second"></a>Pontos de extremidade: chamadas com falha por segundo
Nome do contador: chamadas com falha por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas que retornaram falhas para esse ponto de extremidade em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Em aplicativos Windows Communication Foundation (WCF), os métodos de serviço comunicam informações de erro de processamento usando mensagens de falha SOAP. Falhas de SOAP são tipos de mensagem que são incluídos nos metadados de uma operação de serviço e, portanto, criam um contrato de falha que os clientes podem usar para tornar sua execução mais robusta ou interativa. Como as falhas de SOAP são expressas para clientes em formato XML, elas são altamente interoperáveis.  
  
## <a name="see-also"></a>Veja também

- [Especificando e lidando com falhas em contratos e serviços](../../specifying-and-handling-faults-in-contracts-and-services.md)
