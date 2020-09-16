---
title: Mensagens Confiáveis Ignoradas por Segundo
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: fbc4db354908b45b941799f0352135675293063d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542994"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Mensagens Confiáveis Ignoradas por Segundo
Nome do contador: sessões de mensagens confiáveis eliminadas por segundo.  
  
## <a name="description"></a>Description  
 Número total de mensagens de mensagens confiáveis que foram descartadas neste serviço em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F)
