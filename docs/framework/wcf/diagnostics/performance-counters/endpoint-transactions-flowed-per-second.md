---
title: 'Ponto de extremidade: fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002041"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Ponto de extremidade: fluxo de transações por segundo
Nome do contador: Fluxo de transações por segundo.  
  
## <a name="description"></a>Descrição  
 Número de transações de fluir para operações nesse ponto de extremidade em um segundo. Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem enviada para o ponto de extremidade.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
