---
title: "Threading (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Threading (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Threading permite que seu programa em Visual Basic realizar processamento simultâneo para que você possa fazer mais de uma operação de cada vez. Por exemplo, você pode usar o threading para monitorar a entrada do usuário, executar tarefas em segundo plano e lidar com fluxos simultâneos de entrada.  
  
 Os threads têm as seguintes propriedades:  
  
-   Threads de ativar seu programa para executar processamento simultâneo.  
  
-   O .NET Framework <xref:System.Threading> namespace torna mais fácil o uso de threads.  
  
-   Threads compartilham os recursos do aplicativo. Para obter mais informações, consulte [Usando threads e threading](../Topic/Using%20Threads%20and%20Threading.md).  
  
 Por padrão, um programa Visual Basic tem um thread. No entanto, threads auxiliares podem ser criados e usados para executar código em paralelo com o thread primário. Esses segmentos são chamados *threads de trabalho*.  
  
 Threads de trabalho podem ser usados para executar tarefas demoradas ou críticas sem prender o thread primário. Por exemplo, threads de trabalho são geralmente usados em aplicativos de servidor para atender às solicitações de entrada sem aguardar a solicitação anterior seja concluída. Threads de trabalho também são usados para executar tarefas "em segundo plano" em aplicativos da área de trabalho para que o thread principal – que orienta os elementos de interface do usuário – permanece respondem a ações do usuário.  
  
 Threading resolve problemas com taxa de transferência e a capacidade de resposta, mas ele também pode introduzir problemas de compartilhamento de recursos, como deadlocks e condições de corrida. Vários threads são melhores para tarefas que exigem recursos diferentes, como identificadores de arquivos e conexões de rede. Atribuição de vários threads a um único recurso é pode causar problemas de sincronização e ter threads bloqueados quando aguardando outros threads com freqüência frustra o propósito do uso de vários threads.  
  
 Uma estratégia comum é usar threads de trabalho para executar demorada ou tarefas de tempo crítico que não exigem muitos dos recursos usados por outros threads. Naturalmente, alguns recursos em seu programa devem ser acessados por vários threads. Nesses casos, o <xref:System.Threading> namespace fornece classes para sincronização de threads. Essas classes incluem <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.ManualResetEvent>.  
  
 Você pode usar algumas ou todas essas classes para sincronizar as atividades de vários threads, mas algum suporte para threading é suportado pela linguagem Visual Basic. Por exemplo, o [Instrução SyncLock](../../../../visual-basic/language-reference/statements/synclock-statement.md) fornece recursos de sincronização por meio do uso implícito de <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  Começando com o [!INCLUDE[net_v40_long](../../../../visual-basic/programming-guide/concepts/threading/includes/net_v40_long_md.md)], programação multi\-threaded é bastante simplificada com o <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> e <xref:System.Threading.Tasks.Task?displayProperty=fullName> classes, [LINQ paralelo \(PLINQ\)](../Topic/Parallel%20LINQ%20\(PLINQ\).md), coleta simultânea novas classes a <xref:System.Collections.Concurrent?displayProperty=fullName> namespace e um novo modelo de programação com base no conceito de tarefas em vez de threads. Para obter mais informações, consulte [Programação paralela](../Topic/Parallel%20Programming%20in%20the%20.NET%20Framework.md).  
  
## Tópicos relacionados  
  
|Título|Descrição|  
|------------|---------------|  
|[Aplicativos multithread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)|Descreve como criar e usar threads.|  
|[Parâmetros e valores de retorno para procedimentos multithread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Descreve como passar parâmetros e de retorno com aplicativos multithread.|  
|[Passo a passo: Multithreading com o componente BackgroundWorker \(Visual Basic\)](../Topic/Walkthrough:%20Multithreading%20with%20the%20BackgroundWorker%20Component%20\(Visual%20Basic\).md)|Mostra como criar um aplicativo multithreaded simples.|  
|[Sincronização de thread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)|Descreve como controlar as interações de threads.|  
|[Timers de thread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)|Descreve como executar procedimentos em segmentos separados a intervalos fixos.|  
|[Thread Pooling \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)|Descreve como usar um pool de threads de trabalho que são gerenciados pelo sistema.|  
|[Como: usar um Pool de threads \(Visual Basic\)](../Topic/How%20to:%20Use%20a%20Thread%20Pool%20\(Visual%20Basic\).md)|Demonstra o uso sincronizado de vários threads no pool de threads.|  
|[Threading](../Topic/Managed%20Threading.md)|Descreve como implementar o threading no .NET Framework.|