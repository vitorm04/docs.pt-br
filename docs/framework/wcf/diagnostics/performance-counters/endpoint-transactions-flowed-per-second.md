---
title: 'Ponto de extremidade: fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 9391651eaaca130ef47ddee9daa95b1f8c116892
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553786"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Ponto de extremidade: fluxo de transações por segundo
Nome do contador: transações fluidas por segundo.  
  
## <a name="description"></a>Description  
 Número de transações fluidas para operações neste ponto de extremidade em um segundo. Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem enviada ao ponto de extremidade.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F)
