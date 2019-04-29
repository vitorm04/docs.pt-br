---
title: 'Serviço: Chamadas por segundo'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773302"
---
# <a name="service-calls-per-second"></a>Serviço: Chamadas por segundo
Nome do contador: Chamadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas para esse serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1 de D -D 0) / F) em que o numerador (N) representa o número de operações executadas durante o último intervalo de amostragem, representa o denominador (D) o número de tiques decorrido desde o último intervalo de amostragem, e F é a frequência de tiques.
