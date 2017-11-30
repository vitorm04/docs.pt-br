---
title: "Bloqueando a execução de um aplicativo finalizando uma operação assíncrona"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.openlocfilehash: ccca6e1e4f6b5cdf098018b59426fb2262e2b346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Bloqueando a execução de um aplicativo finalizando uma operação assíncrona
Aplicativos que não podem continuar a executar outras tarefas enquanto aguarda os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída. Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar uma operação assíncrona concluir:  
  
-   Chamar operações assíncronas **final** *OperationName* método. Essa abordagem é demonstrada neste tópico.  
  
-   Use o <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriedade o <xref:System.IAsyncResult> retornado da operação assíncrona **começar** *OperationName* método. Para obter um exemplo que demonstra essa abordagem, consulte [bloqueando a execução de aplicativo com um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplicativos que usam o **final** *OperationName* normalmente será chamada de método para bloquear até que uma operação assíncrona é concluída a **começar**  *OperationName* método, executar qualquer trabalho que pode ser feito sem os resultados da operação e, em seguida, chamar **final** *OperationName*.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos no <xref:System.Net.Dns> classe para recuperar informações do sistema de nomes de domínio para um computador especificado pelo usuário. Observe que `null` (`Nothing` no Visual Basic) é passada o <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` e `stateObject` parâmetros porque esses argumentos não são necessários ao usar essa abordagem.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
