---
title: Mensagens suspeitas na fila por segundo
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="queued-poison-messages-per-second"></a>Mensagens suspeitas na fila por segundo
Nome do contador: Na fila de mensagens suspeitas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de mensagens que são marcadas como suspeitas pelo transporte em fila neste serviço em um segundo.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (1 - N 0 N) / ((D - 1D 0) / F)
