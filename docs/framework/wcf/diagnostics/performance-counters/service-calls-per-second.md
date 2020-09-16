---
title: 'Serviço: chamadas por segundo'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5066108d8183502eeaec7c25186c00d9978261b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546927"
---
# <a name="service-calls-per-second"></a>Serviço: chamadas por segundo
Nome do contador: chamadas por segundo.  
  
## <a name="description"></a>Description  
 Número de chamadas para esse serviço em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F) em que o numerador (N) representa o número de operações executadas durante o último intervalo de amostragem, o denominador (D) representa o número de tiques decorridos durante o último intervalo de amostragem e F é a frequência das tiques.
