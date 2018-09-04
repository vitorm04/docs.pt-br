---
title: 'Serviço: chamadas por segundo'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499881"
---
# <a name="service-calls-per-second"></a>Serviço: chamadas por segundo
Nome do contador: Chamadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas para esse serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1 de D -D 0) / F) em que o numerador (N) representa o número de operações executadas durante o último intervalo de amostragem, representa o denominador (D) o número de tiques decorrido desde o último intervalo de amostragem, e F é a frequência de tiques.
