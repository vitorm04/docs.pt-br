---
title: Programando threads
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e1fb7d61b8e250884b2c57cad8c5106bc77787a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="scheduling-threads"></a>Programando threads
Cada thread tem uma prioridade de thread atribuída a ele. Threads criados dentro do common language runtime inicialmente atribuídas a prioridade de **ThreadPriority.Normal**. Threads criados fora do tempo de execução retêm a prioridade que tinham antes de ele inseriu o ambiente gerenciado. Você pode obter ou definir a prioridade de qualquer thread com o **Thread.Priority** propriedade.  
  
 Threads são agendados para execução com base em sua prioridade. Mesmo que os threads estão em execução no tempo de execução, todos os threads são atribuídos frações de tempo do processador, o sistema operacional. Os detalhes do agendamento algoritmo usado para determinar a ordem na qual os threads são executados varia de acordo com cada sistema operacional. Em alguns sistemas operacionais, o thread com a prioridade mais alta (esses threads que podem ser executadas) sempre está programado para ser executado primeiro. Se vários threads com a mesma prioridade estão disponíveis, o Agendador percorre os threads com prioridade, fornecendo uma fatia de tempo fixo no qual executar de cada thread. Como um thread com uma prioridade mais alta estiver disponível para ser executado, não obtém executar threads de prioridade inferior. Quando há mais nenhum executáveis threads em uma determinada prioridade, o Agendador move para a próxima prioridade mais baixa e agendas de threads com prioridade para a execução. Se um thread de prioridade mais alto se torne executável, o thread de prioridade mais baixo é apropriado e o thread de prioridade mais alto pode ser executado novamente. Acima de tudo isso, o sistema operacional também pode ajustar as prioridades de thread dinamicamente como interface de usuário do aplicativo é movido entre o primeiro e segundo plano. Outros sistemas operacionais podem optar por usar um algoritmo de programação diferente.  
  
## <a name="see-also"></a>Consulte também  
 [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Threading gerenciado e não gerenciado no Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
