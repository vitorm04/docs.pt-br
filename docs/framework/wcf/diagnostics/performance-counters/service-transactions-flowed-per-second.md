---
title: 'Serviço: fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: 2ed9f6711c998bbd3f1130b9a91d8ac850821a07
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559318"
---
# <a name="service-transactions-flowed-per-second"></a>Serviço: fluxo de transações por segundo
Nome do contador: transações fluidas por segundo.  
  
## <a name="description"></a>Description  
 Número de transações fluidas para operações neste serviço em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F)
