---
title: Threading (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e3f213b43c2f05a5afef1db7aec8b9c2695df989
ms.contentlocale: pt-br
ms.lasthandoff: 06/12/2017

---
# <a name="threading-c"></a>Threading (C#)
O threading permite que seu programa em C# execute processamento simultâneo para que você possa fazer mais de uma operação de cada vez. Por exemplo, você pode usar o threading para monitorar a entrada do usuário, executar tarefas em segundo plano e lidar com fluxos simultâneos de entrada.  
  
 Os threads têm as seguintes propriedades:  
  
-   Eles permitem que seu programa execute processamento simultâneo.  
  
-   O .NET Framework <xref:System.Threading> torna namespace usando threads mais fácil.  
  
-   Os threads compartilham os recursos do aplicativo. Para obter mais informações, consulte [Usando threads e threading](https://msdn.microsoft.com/library/e1dx6b2h).  
  
 Por padrão, um programa em C# tem um thread. No entanto, threads auxiliares podem ser criados e usados para executar código em paralelo com o thread primário. Esses segmentos são chamados de *threads de trabalho*.  
  
 Os threads de trabalho podem ser usados para executar tarefas demoradas ou críticas sem prender o thread primário. Por exemplo, threads de trabalho são geralmente usados em aplicativos de servidor para atender às solicitações de entrada sem aguardar a solicitação anterior seja concluída. Os threads de trabalho também são usados para executar tarefas "em segundo plano" em aplicativos da área de trabalho para que o thread principal – que orienta os elementos da interface do usuário – permaneçam responsivos às ações do usuário.  
  
 O threading resolve problemas com taxa de transferência e capacidade de resposta, mas ele também pode introduzir problemas de compartilhamento de recursos, como deadlocks e condições de corrida. Vários threads são melhores para tarefas que exigem recursos diferentes, como identificadores de arquivos e conexões de rede. A atribuição de vários threads a um único recurso pode causar problemas de sincronização e ter threads bloqueados com frequência ao aguardar outros threads frustra o propósito do uso de vários threads.  
  
 Uma estratégia comum é usar threads de trabalho para executar tarefas demoradas ou tarefas de tempo crítico que não exigem muitos dos recursos usados por outros threads. Naturalmente, alguns recursos em seu programa devem ser acessados por vários threads. Para esses casos, o <xref:System.Threading> namespace fornece classes para sincronização de threads. Essas classes incluem <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.ManualResetEvent>.  
  
 Você pode usar algumas ou todas essas classes para sincronizar as atividades de vários threads, mas é dado suporte para threading pela linguagem C#. Por exemplo, o [instrução Lock](../../../../csharp/language-reference/keywords/lock-statement.md) fornece recursos de sincronização por meio do uso implícito de <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  Começando com o [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], programação multi-threaded é bastante simplificada com o <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> e <xref:System.Threading.Tasks.Task?displayProperty=fullName> classes, [LINQ paralelo (PLINQ)](https://msdn.microsoft.com/library/dd460688), nova coleção simultânea classes o <xref:System.Collections.Concurrent?displayProperty=fullName> namespace e um novo modelo de programação que se baseia o conceito de tarefas em vez de threads. Para obter mais informações, consulte [Programação paralela](https://msdn.microsoft.com/library/dd460693).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Aplicativos com multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|Descreve como criar e usar um threads.|  
|[Parâmetros e valores de retorno para procedimentos multi-threaded (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Descreve como passar e retornar parâmetros com aplicativos multi-threaded.|  
|[Instruções passo a passo: multithreading com o componente BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Mostra como criar um aplicativo multi-threaded simples.|  
|[Sincronização de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|Descreve como controlar as interações de threads.|  
|[Temporizadores de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|Descreve como executar procedimentos em threads separados em intervalos fixos.|  
|[Pooling de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|Descreve como usar um pool de threads de trabalho que são gerenciados pelo sistema.|  
|[Como usar um pool de thread (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Demonstra o uso sincronizado de vários threads no pool de threads.|  
|[Threading](https://msdn.microsoft.com/library/3e8s7xdd)|Descreve como implementar o threading no .NET Framework.|
