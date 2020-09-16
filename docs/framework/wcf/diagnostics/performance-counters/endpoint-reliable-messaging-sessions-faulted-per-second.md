---
title: 'Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 118b6a68903f6550cb78f10ad953447e86f5cd3e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550222"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo
Nome do contador: sessões de mensagens confiáveis com falha por segundo.  
  
## <a name="description"></a>Description  
 Número de sessões de mensagens confiáveis com falha neste ponto de extremidade em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F)
