---
title: Bloqueando a execução de um aplicativo finalizando uma operação assíncrona
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: d457a9c22f0eaea02fe744ebb24d02558710948b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64629019"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Bloqueando a execução de um aplicativo finalizando uma operação assíncrona
Aplicativos que não continuem a executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída. Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar a conclusão de uma operação assíncrona:  
  
- Chame o método **End**_OperationName_ das operações assíncronas. Esta abordagem será demonstrada neste tópico.  
  
- Use a propriedade <xref:System.IAsyncResult.AsyncWaitHandle%2A> do <xref:System.IAsyncResult> retornado pelo método **Begin**_OperationName_ da operação assíncrona. Para obter um exemplo que demonstra essa abordagem, consulte [Bloqueando a execução de um aplicativo com um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Os aplicativos que usarem o método **End**_OperationName_ para bloqueio até a conclusão de uma operação assíncrona normalmente chamarão o método **Begin**_OperationName_, executarão qualquer trabalho que possa ser feito sem os resultados da operação e, em seguida, chamarão **End**_OperationName_.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do Sistema de Nomes de Domínio de computadores especificados pelo usuário. Observe que `null` (`Nothing` no Visual Basic) é passado para os parâmetros <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` e `stateObject` porque esses argumentos não são necessários ao usar essa abordagem.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
