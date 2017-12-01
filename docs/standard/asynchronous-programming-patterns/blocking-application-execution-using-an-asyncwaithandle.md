---
title: "Bloqueando a execução de aplicativos com um AsyncWaitHandle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Bloqueando a execução de aplicativos com um AsyncWaitHandle
Aplicativos que não podem continuar a executar outras tarefas enquanto aguarda os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída. Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar uma operação assíncrona concluir:  
  
-   Use o <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriedade o <xref:System.IAsyncResult> retornado da operação assíncrona **começar** *OperationName* método. Essa abordagem é demonstrada neste tópico.  
  
-   Chame a operação assíncrona **final** *OperationName* método. Para obter um exemplo que demonstra essa abordagem, consulte [bloqueando a execução de aplicativos por finalizando uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplicativos que usam um ou mais <xref:System.Threading.WaitHandle> objetos para bloquear até que uma operação assíncrona é concluída normalmente chamará o **começar** *OperationName* método, executar qualquer trabalho que pode ser feito sem os resultados da operação e, em seguida, bloco até que as operações assíncronas é concluída. Um aplicativo pode bloquear em uma única operação chamando um do <xref:System.Threading.WaitHandle.WaitOne%2A> métodos usando o <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Para bloquear durante a espera para um conjunto de operações assíncronas sejam concluídas, armazenar associado <xref:System.IAsyncResult.AsyncWaitHandle%2A> objetos em uma matriz e a chamada do <xref:System.Threading.WaitHandle.WaitAll%2A> métodos. Para bloquear enquanto aguarda a qualquer um de um conjunto de operações assíncronas sejam concluídas, armazenar associado <xref:System.IAsyncResult.AsyncWaitHandle%2A> objetos em uma matriz e a chamada do <xref:System.Threading.WaitHandle.WaitAny%2A> métodos.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos na classe de DNS para recuperar informações do sistema de nomes de domínio para um computador especificado pelo usuário. O exemplo demonstra o bloqueio usando a <xref:System.Threading.WaitHandle> associados com a operação assíncrona. Observe que `null` (`Nothing` no Visual Basic) é passada o <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` e `stateObject` parâmetros porque eles não são necessários ao usar essa abordagem.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
