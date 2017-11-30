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
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="e301e-102">Bloqueando a execução de um aplicativo finalizando uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="e301e-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="e301e-103">Aplicativos que não podem continuar a executar outras tarefas enquanto aguarda os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="e301e-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="e301e-104">Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar uma operação assíncrona concluir:</span><span class="sxs-lookup"><span data-stu-id="e301e-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="e301e-105">Chamar operações assíncronas **final** *OperationName* método.</span><span class="sxs-lookup"><span data-stu-id="e301e-105">Call the asynchronous operations **End** *OperationName* method.</span></span> <span data-ttu-id="e301e-106">Essa abordagem é demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e301e-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="e301e-107">Use o <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriedade o <xref:System.IAsyncResult> retornado da operação assíncrona **começar** *OperationName* método.</span><span class="sxs-lookup"><span data-stu-id="e301e-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="e301e-108">Para obter um exemplo que demonstra essa abordagem, consulte [bloqueando a execução de aplicativo com um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="e301e-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="e301e-109">Aplicativos que usam o **final** *OperationName* normalmente será chamada de método para bloquear até que uma operação assíncrona é concluída a **começar**  *OperationName* método, executar qualquer trabalho que pode ser feito sem os resultados da operação e, em seguida, chamar **final** *OperationName*.</span><span class="sxs-lookup"><span data-stu-id="e301e-109">Applications that use the **End** *OperationName* method to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then call **End** *OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e301e-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e301e-110">Example</span></span>  
 <span data-ttu-id="e301e-111">O exemplo de código a seguir demonstra como usar métodos assíncronos no <xref:System.Net.Dns> classe para recuperar informações do sistema de nomes de domínio para um computador especificado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e301e-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="e301e-112">Observe que `null` (`Nothing` no Visual Basic) é passada o <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` e `stateObject` parâmetros porque esses argumentos não são necessários ao usar essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="e301e-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e301e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e301e-113">See Also</span></span>  
 [<span data-ttu-id="e301e-114">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="e301e-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="e301e-115">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="e301e-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
