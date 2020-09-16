---
title: Mensagens suspeitas na fila por segundo
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 39118b515949e6ad4f6ff651037cd757a6dd9bbf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552642"
---
# <a name="queued-poison-messages-per-second"></a>Mensagens suspeitas na fila por segundo
Nome do contador: mensagens suspeitas enfileiradas por segundo.  
  
## <a name="description"></a>Description  
 Número de mensagens marcadas como inviabilizada pelo transporte em fila neste serviço em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F)
