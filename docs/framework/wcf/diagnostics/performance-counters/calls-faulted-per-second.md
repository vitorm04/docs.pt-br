---
title: Chamadas com falha por segundo
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: af84a379a36324131861aaa7e8577b5a44273917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471335"
---
# <a name="calls-faulted-per-second"></a>Chamadas com falha por segundo
Nome do contador: Chamadas com falha por segundo  
  
## <a name="description"></a>Descrição  
 Número de chamadas que retornaram falhas para essa operação em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (1 - N 0 N) / ((D - 1D 0) / F)  
  
 Aplicativos do Windows Communication Foundation (WCF), métodos de serviço se comunicam informações de erro de processamento usando mensagens de falha SOAP. Falhas de SOAP são tipos de mensagem que estão incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar a execução mais robusta ou interativo. Como falhas de SOAP são demonstradas para clientes em formato XML, eles são altamente interoperáveis.  
  
## <a name="see-also"></a>Consulte também  
 [Especificando e lidando com falhas em contratos e serviços](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
