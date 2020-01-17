---
title: Mensagens Confiáveis Ignoradas por Segundo
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 946e0408b8b6602bba7824b45e4d6cb91cdaa4eb
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163950"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Mensagens Confiáveis Ignoradas por Segundo
Nome do contador: sessões de mensagens confiáveis eliminadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número total de mensagens de mensagens confiáveis que foram descartadas neste serviço em um segundo.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
