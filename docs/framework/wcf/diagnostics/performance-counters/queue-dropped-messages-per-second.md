---
title: Mensagens da fila ignoradas por segundo
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528117"
---
# <a name="queue-dropped-messages-per-second"></a>Mensagens da fila ignoradas por segundo
Nome do contador: Na fila de mensagens descartadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de mensagens que serão descartadas pelo transporte enfileirado neste serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
