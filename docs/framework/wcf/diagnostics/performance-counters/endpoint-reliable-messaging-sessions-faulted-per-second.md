---
title: 'Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 26fd8236af6516716f7cf9c7c06f669473bdfc3a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163183"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo
Nome do contador: sessões de mensagens confiáveis com falha por segundo.  
  
## <a name="description"></a>Descrição  
 Número de sessões de mensagens confiáveis com falha neste ponto de extremidade em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
