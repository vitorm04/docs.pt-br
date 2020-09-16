---
title: Chamadas com falha por segundo
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 8f2337d5ea3eb696c7be5b25d01396676dae2458
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554111"
---
# <a name="calls-failed-per-second"></a>Chamadas com falha por segundo
Nome do contador: chamadas com falha por segundo  
  
## <a name="description"></a>Description  
 Número de chamadas com exceções sem tratamento nesta operação em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Esse contador é incrementado toda vez que há uma exceção sem tratamento nesta operação.  
  
## <a name="see-also"></a>Confira também

- [Especificando e lidando com falhas em contratos e serviços](../../specifying-and-handling-faults-in-contracts-and-services.md)
