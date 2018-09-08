---
title: 'Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: f6b48ec4c37c28588dd874a5bfa94a01a2f43b0c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190813"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo
Nome do contador: Sessões de Reliable Messaging com falha por segundo.  
  
## <a name="description"></a>Descrição  
 Número de sessões de reliable messaging com falha neste ponto de extremidade em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
