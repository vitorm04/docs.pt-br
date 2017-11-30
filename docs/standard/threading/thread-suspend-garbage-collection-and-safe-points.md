---
title: Thread.Suspend, coleta de lixo e pontos seguros
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend, coleta de lixo e pontos seguros
Quando você chama <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> em um thread, o sistema observa que a suspensão de um thread foi solicitada e permite a execução até que ele atingiu um ponto de segurança antes de realmente suspender o thread do thread. Um ponto de segurança para um thread é um ponto em sua execução de coleta de lixo pode ser executada.  
  
 Quando um ponto de segurança é atingido, o tempo de execução garante que o thread suspenso não fará qualquer progresso adicional em código gerenciado. Um thread de execução fora do código gerenciado é sempre seguro para coleta de lixo e a execução continua até que ele tentará retomar a execução de código gerenciado.  
  
> [!NOTE]
>  Para executar uma coleta de lixo, tempo de execução deve suspender todos os threads exceto o thread de execução de coleta. Cada segmento deve ser colocado em um ponto de segurança antes de poder ser suspenso.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Gerenciamento Automático de Memória](../../../docs/standard/automatic-memory-management.md)
