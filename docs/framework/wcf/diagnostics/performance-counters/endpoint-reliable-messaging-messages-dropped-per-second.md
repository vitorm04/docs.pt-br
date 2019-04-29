---
title: 'Ponto de extremidade: Mensagens Confiáveis Ignoradas por Segundo'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797196"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a>Ponto de extremidade: Mensagens Confiáveis Ignoradas por Segundo
Nome do contador: Sessões de Reliable Messaging eliminados por segundo.  
  
## <a name="description"></a>Descrição  
 Número total de mensagens confiáveis que foram descartados nesse ponto de extremidade em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
