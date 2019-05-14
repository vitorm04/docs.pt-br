---
title: Noções básicas de threading gerenciado
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b352c35a327ed4736a1f41816d3f15c1a0f559f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644814"
---
# <a name="managed-threading-basics"></a>Noções básicas de threading gerenciado

Os cinco primeiros tópicos desta seção destinam-se a ajudá-lo a determinar quando usar o threading gerenciado e explicar algumas funcionalidades básicas. Para obter informações sobre as classes que fornecem recursos adicionais, confira [Recursos e objetos de threading](../../../docs/standard/threading/threading-objects-and-features.md) e [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 O restante dos tópicos desta seção abordam tópicos avançados, incluindo a interação de threading gerenciado com o sistema operacional Windows.  
  
> [!NOTE]
>  No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a biblioteca de paralelismo de tarefas e o PLINQ fornecem APIs para o paralelismo de tarefa e dados em programas multithreading. Para obter mais informações, consulte [Programação paralela](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Nesta seção

 [Threads e threading](../../../docs/standard/threading/threads-and-threading.md)  
 São discutidas as vantagens e desvantagens de vários threads e são descritos os cenários em que você pode criar threads ou usar threads de pool.  
  
 [Exceções em threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 É descrito o comportamento de exceções sem tratamento em threads para diferentes versões do .NET Framework, em particular as situações em que elas resultam no encerramento do aplicativo.  
  
 [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 São descritas as estratégias para sincronizar dados em classes que serão usadas com vários threads.  
  
 [Threads em primeiro plano e em segundo plano](../../../docs/standard/threading/foreground-and-background-threads.md)  
 São explicadas as diferenças entre os threads de primeiro plano e segundo plano.  
  
 [Threading gerenciado e não gerenciado no Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 É discutido o relacionamento entre o threading gerenciado e não gerenciado, são listados os equivalentes gerenciados para APIs de threading do Windows e é discutida a interação de apartments COM e threads gerenciados.  
  
 [Armazenamento local de thread: Campos estáticos relativos a thread e slots de dados](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 São descritos os mecanismos de armazenamento relativos a threads.  
  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 É descrito como operações assíncronas ou síncronas de longa execução podem ser canceladas usando um token de cancelamento.  
  
## <a name="reference"></a>Referência

 <xref:System.Threading.Thread>  
 Fornece documentação de referência para a classe **Thread**, que representa um thread gerenciado, seja ele proveniente de código não gerenciado ou criado em um aplicativo gerenciado.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 É fornecida uma maneira segura de implementar multithreading juntamente com objetos de interface do usuário.  
  
## <a name="related-sections"></a>Seções relacionadas

 [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 São descritas as classes gerenciadas usadas para sincronizar as atividades de vários threads.  
  
 [Práticas recomendadas de threading gerenciado](../../../docs/standard/threading/managed-threading-best-practices.md)  
 São descritos problemas comuns com o multithreading e estratégias para evitar problemas.  
  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 É descrita a biblioteca de paralelismo de tarefas e o PLINQ, que simplifica muito o trabalho de criação de aplicativos do .NET Framework de multithreading e assíncronos.
