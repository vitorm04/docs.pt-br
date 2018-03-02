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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdd56763712dee9c6fa1f292eb3bbb2f0ccbf505
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend, coleta de lixo e pontos seguros
Quando você chama <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> em um thread, o sistema observa que uma suspensão de thread foi solicitada e permite que o thread seja executado até atingir um ponto seguro antes de realmente suspendê-lo. Um ponto seguro de um thread é um ponto da execução em que a coleta de lixo pode ser executada.  
  
 Quando um ponto seguro é alcançado, o tempo de execução garante que o thread suspenso não fará mais progresso no código gerenciado. Um thread que é executado fora do código gerenciado está sempre seguro para a coleta de lixo e sua execução continua até que ele tente retomar a execução do código gerenciado.  
  
> [!NOTE]
>  Para executar uma coleta de lixo, o tempo de execução deve suspender todos os threads exceto o thread que executa a coleta. Cada thread deve ser colocado em um ponto seguro antes de poder ser suspenso.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Gerenciamento Automático de Memória](../../../docs/standard/automatic-memory-management.md)
