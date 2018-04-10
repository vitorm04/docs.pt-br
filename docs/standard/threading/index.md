---
title: Threading gerenciado
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 43fe5f9d193de3f48abfc0d91e01a70ee601a651
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="managed-threading"></a>Threading gerenciado
Quer você esteja desenvolvendo para computadores com um processador, quer para com vários, é conveniente que seu aplicativo forneça uma interação mais dinâmica com o usuário, mesmo se o aplicativo, no momento, estiver realizando outro trabalho. Usar vários threads de execução é uma das maneiras mais eficazes de manter seu aplicativo responsivo ao usuário e, ao mesmo tempo, usar o processador entre ou, até mesmo, durante os eventos do usuário. Embora esta seção introduza os conceitos básicos de threading, ele se concentra nos conceitos de threading gerenciado e em como usá-lo.  
  
> [!NOTE]
>  A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a programação multi-threaded é bastante simplificada com as classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [PLINQ (LINQ Paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), novas classes de coleta simultânea no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType> e um novo modelo de programação com base no conceito de tarefas em vez de threads. Para obter mais informações, consulte [Programação paralela](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Noções básicas de threading gerenciado](../../../docs/standard/threading/managed-threading-basics.md)  
 Fornece uma visão geral de threading gerenciado e descreve quando usar vários threads.  
  
 [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 Explica como criar, iniciar, pausar, retomar e abortar threads.  
  
 [Práticas recomendadas de threading gerenciado](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Aborda os níveis de sincronização, como evitar deadlocks e condições de corrida, computadores com único processador e vários processadores, além de outros problemas de threading.  
  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 Descreve as classes gerenciadas que você pode usar para sincronizar as atividades de threads e os dados de objetos acessados em threads diferentes, bem como fornece uma visão geral dos threads de pool do thread.  
  
## <a name="reference"></a>Referência  
 <xref:System.Threading>  
 Contém classes para uso e sincronização de threads gerenciados.  
  
 <xref:System.Collections.Concurrent>  
 Contém classes de coleção que são seguras para uso com vários threads.  
  
 <xref:System.Threading.Tasks>  
 Contém classes para criação e agendamento de tarefas de processamento simultâneo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Domínios do aplicativo](../../../docs/framework/app-domains/application-domains.md)  
 Fornece uma visão geral de domínios do aplicativo e seu uso pelo Common Language Infrastructure.  
  
 [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Descreve as vantagens de desempenho e a operação básica da E/S assíncrona.  
  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Fornece uma visão geral da programação assíncrona.  
  
 [Chamando métodos síncronos de forma assíncrona](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Explica como chamar métodos nos threads de pool do thread usando recursos internos de representantes.  
  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 Descreve as bibliotecas de programação paralela, que simplificam o uso de vários threads em aplicativos.  
  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Descreve um sistema para executar consultas paralelamente, de modo a aproveitar vários processadores.
