---
title: Mensagens Confiáveis Ignoradas por Segundo
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916026"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Mensagens Confiáveis Ignoradas por Segundo
Nome do contador: Sessões de Reliable Messaging eliminados por segundo.  
  
## <a name="description"></a>Descrição  
 Número total de mensagens confiáveis que foram ignoradas neste serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
