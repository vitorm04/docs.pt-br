---
title: Operações Transacionadas em Dúvida por Segundo
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46005681"
---
# <a name="transacted-operations-in-doubt-per-second"></a>Operações Transacionadas em Dúvida por Segundo
Nome do contador: Operações transacionadas em dúvida por segundo.  
  
## <a name="description"></a>Descrição  
 Número de operações transacionais com resultados em dúvida neste serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
