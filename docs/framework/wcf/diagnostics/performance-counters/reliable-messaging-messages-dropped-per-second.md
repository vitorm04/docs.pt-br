---
title: Mensagens confiáveis do sistema de mensagens descartadas por segundo
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075378"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Mensagens confiáveis do sistema de mensagens descartadas por segundo
Nome do contador: Sessões de Reliable Messaging eliminados por segundo.  
  
## <a name="description"></a>Descrição  
 Número total de mensagens confiáveis que foram ignoradas neste serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
