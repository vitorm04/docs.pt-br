---
title: Threading (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c1875a63ab7f5104f7b8c2d39a16499b289d9a50
ms.lasthandoff: 03/13/2017

---
# <a name="threading-visual-basic"></a>Threading (Visual Basic)
O threading permite que seu programa do Visual Basic execute processamento simultâneo para que você possa fazer mais de uma operação de cada vez. Por exemplo, você pode usar o threading para monitorar a entrada do usuário, executar tarefas em segundo plano e lidar com fluxos simultâneos de entrada.  
  
 Os threads têm as seguintes propriedades:  
  
-   Eles permitem que seu programa execute processamento simultâneo.  
  
-   O namespace <xref:System.Threading> do .NET Framework facilita o uso de threads.  
  
-   Os threads compartilham os recursos do aplicativo. Para obter mais informações, consulte [Usando threads e threading](https://msdn.microsoft.com/library/e1dx6b2h).  
  
 Por padrão, um programa do Visual Basic tem um thread. No entanto, threads auxiliares podem ser criados e usados para executar código em paralelo com o thread primário. Esses segmentos são chamados de *threads de trabalho*.  
  
 Os threads de trabalho podem ser usados para executar tarefas demoradas ou críticas sem prender o thread primário. Por exemplo, threads de trabalho são geralmente usados em aplicativos de servidor para atender às solicitações de entrada sem aguardar a solicitação anterior seja concluída. Os threads de trabalho também são usados para executar tarefas "em segundo plano" em aplicativos da área de trabalho para que o thread principal – que orienta os elementos da interface do usuário – permaneçam responsivos às ações do usuário.  
  
 O threading resolve problemas com taxa de transferência e capacidade de resposta, mas ele também pode introduzir problemas de compartilhamento de recursos, como deadlocks e condições de corrida. Vários threads são melhores para tarefas que exigem recursos diferentes, como identificadores de arquivos e conexões de rede. A atribuição de vários threads a um único recurso pode causar problemas de sincronização e ter threads bloqueados com frequência ao aguardar outros threads frustra o propósito do uso de vários threads.  
  
 Uma estratégia comum é usar threads de trabalho para executar tarefas demoradas ou tarefas de tempo crítico que não exigem muitos dos recursos usados por outros threads. Naturalmente, alguns recursos em seu programa devem ser acessados por vários threads. Nesses casos, o namespace <xref:System.Threading> fornece classes para sincronização de threads. Essas classes incluem <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent>.  
  
 Você pode usar algumas ou todas essas classes para sincronizar as atividades de vários threads, mas o suporte para threading é dado pela linguagem do Visual Basic. Por exemplo, a [instrução SyncLock](../../../../visual-basic/language-reference/statements/synclock-statement.md) fornece recursos de sincronização por meio do uso implícito de <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  Iniciando do [!INCLUDE[net_v40_long](../../../../csharp/programming-guide/concepts/threading/includes/net_v40_long_md.md)], a programação multi-threaded é bastante simplificada com as classes <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> e <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), novas classes de coleta simultânea no namespace <xref:System.Collections.Concurrent?displayProperty=fullName> e um novo modelo de programação com base no conceito de tarefas em vez de threads. Para obter mais informações, consulte [Programação paralela](https://msdn.microsoft.com/library/dd460693).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Aplicativos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)|Descreve como criar e usar um threads.|  
|[Parâmetros e valores de retorno para procedimentos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Descreve como passar e retornar parâmetros com aplicativos multi-threaded.|  
|[Instruções passo a passo: multithreading com o componente BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Mostra como criar um aplicativo multi-threaded simples.|  
|[Sincronização de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)|Descreve como controlar as interações de threads.|  
|[Temporizadores de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)|Descreve como executar procedimentos em threads separados em intervalos fixos.|  
|[Pooling de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)|Descreve como usar um pool de threads de trabalho que são gerenciados pelo sistema.|  
|[Como usar um pool de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Demonstra o uso sincronizado de vários threads no pool de threads.|  
|[Threading](https://msdn.microsoft.com/library/3e8s7xdd)|Descreve como implementar o threading no .NET Framework.|
