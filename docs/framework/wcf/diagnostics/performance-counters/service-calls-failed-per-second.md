---
title: 'Serviços: chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 6af8f79d1fe163967a5c6e8220697aa11bee66c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="service-calls-failed-per-second"></a>Serviços: chamadas com falha por segundo
Nome do contador: Chamadas com falha por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas que têm exceções sem tratamento e são recebidas por este serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (1 - N 0 N) / ((D - 1D 0) / F)  
  
 No código gerenciado, as exceções são geradas quando ocorrem condições de erro.  
  
 No código gerenciado, as exceções são geradas quando ocorrem condições de erro.  
  
 Esse contador é incrementado toda vez que há uma exceção sem tratamento neste serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Especificando e lidando com falhas em contratos e serviços](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
