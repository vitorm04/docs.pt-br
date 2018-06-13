---
title: Operações Transacionadas Anuladas por Segundo
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: dacdf93f4610df9161134a41ece19fd2a18637c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474526"
---
# <a name="transacted-operations-aborted-per-second"></a>Operações Transacionadas Anuladas por Segundo
Nome do contador: Transacionado operações anuladas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de operações transacionais anulados neste serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (1 - N 0 N) / ((D - 1D 0) / F)
