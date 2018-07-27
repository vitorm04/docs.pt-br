---
title: Threading (C#)
ms.date: 07/20/2015
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
ms.openlocfilehash: f9ba0793876f38b3ada2f65c4594562ea1a66983
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39296176"
---
# <a name="threading-c"></a>Threading (C#)
O threading permite que seu programa em C# execute processamento simultâneo para que você possa fazer mais de uma operação de cada vez. Por exemplo, você pode usar o threading para monitorar a entrada do usuário, executar tarefas em segundo plano e lidar com fluxos simultâneos de entrada.  
  
 Os threads têm as seguintes propriedades:  
  
-   Eles permitem que seu programa execute processamento simultâneo.  
  
-   O namespace do .NET Framework <xref:System.Threading> facilita o uso de threads.  
  
-   Os threads compartilham os recursos do aplicativo. Para obter mais informações, consulte [Usando threads e threading](../../../../../docs/standard/threading/using-threads-and-threading.md).  
  
 Por padrão, um programa em C# tem um thread. No entanto, threads auxiliares podem ser criados e usados para executar código em paralelo com o thread primário. Esses segmentos são chamados de *threads de trabalho*.  
  
 Os threads de trabalho podem ser usados para executar tarefas demoradas ou críticas sem prender o thread primário. Por exemplo, threads de trabalho são geralmente usados em aplicativos de servidor para atender às solicitações de entrada sem aguardar a solicitação anterior seja concluída. Os threads de trabalho também são usados para executar tarefas "em segundo plano" em aplicativos da área de trabalho para que o thread principal – que orienta os elementos da interface do usuário – permaneçam responsivos às ações do usuário.  
  
 O threading resolve problemas com taxa de transferência e capacidade de resposta, mas ele também pode introduzir problemas de compartilhamento de recursos, como deadlocks e condições de corrida. Vários threads são melhores para tarefas que exigem recursos diferentes, como identificadores de arquivos e conexões de rede. A atribuição de vários threads a um único recurso pode causar problemas de sincronização e ter threads bloqueados com frequência ao aguardar outros threads frustra o propósito do uso de vários threads.  
  
 Uma estratégia comum é usar threads de trabalho para executar tarefas demoradas ou tarefas de tempo crítico que não exigem muitos dos recursos usados por outros threads. Naturalmente, alguns recursos em seu programa devem ser acessados por vários threads. Nesses casos, o namespace <xref:System.Threading> fornece classes para sincronização de threads. Essas classes incluem <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent>.  
  
 Você pode usar algumas ou todas essas classes para sincronizar as atividades de vários threads, mas é dado suporte para threading pela linguagem C#. Por exemplo, a [Instrução lock](../../../../csharp/language-reference/keywords/lock-statement.md) fornece recursos de sincronização por meio do uso implícito de <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  A partir do [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], a programação multi-threaded é bastante simplificada com as classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, o [PLINQ (LINQ Paralelo)](https://msdn.microsoft.com/library/dd460688), as novas classes de coleta simultânea no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType> e um novo modelo de programação com base no conceito de tarefas em vez de threads. Para obter mais informações, consulte [Programação paralela](../../../../../docs/standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Aplicativos com multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|Descreve como criar e usar um threads.|  
|[Sincronização de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|Descreve como controlar as interações de threads.|  
|[Pooling de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|Descreve como usar um pool de threads de trabalho que são gerenciados pelo sistema.|  
|[Como usar um pool de thread (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Demonstra o uso sincronizado de vários threads no pool de threads.|  
|[Threading](../../../../../docs/standard/threading/index.md)|Descreve como implementar o threading no .NET Framework.|
