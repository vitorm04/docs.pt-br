---
title: Sessões de Mensagens Confiáveis com Falha por Segundo
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44704963"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a>Sessões de Mensagens Confiáveis com Falha por Segundo
Nome do contador: Sessões de Reliable Messaging com falha por segundo.  
  
## <a name="description"></a>Descrição  
 Número de sessões de reliable messaging com falha neste serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
