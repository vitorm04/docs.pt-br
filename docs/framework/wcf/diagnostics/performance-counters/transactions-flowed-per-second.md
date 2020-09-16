---
title: Fluxo de transações por segundo
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: d55856a5d820df2c668863a2a3e853995a113143
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552200"
---
# <a name="transactions-flowed-per-second"></a>Fluxo de transações por segundo
Nome do contador: transações fluidas por segundo  
  
## <a name="description"></a>Description  
 Número de transações fluidas para esta operação em um segundo. Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem que é enviada para a operação.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1-N 0)/((D 1-D 0)/F)
