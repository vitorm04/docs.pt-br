---
title: Bloqueando a execução de um aplicativo finalizando uma operação assíncrona
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ec7bfe6fe2cef20a6d74030802113a47e8679e1
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="79a5b-102">Bloqueando a execução de um aplicativo finalizando uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="79a5b-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="79a5b-103">Aplicativos que não continuem a executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="79a5b-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="79a5b-104">Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar a conclusão de uma operação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="79a5b-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="79a5b-105">Chame o método **End***OperationName* de operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="79a5b-105">Call the asynchronous operations **End***OperationName* method.</span></span> <span data-ttu-id="79a5b-106">Esta abordagem será demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="79a5b-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="79a5b-107">Use a propriedade <xref:System.IAsyncResult.AsyncWaitHandle%2A> do <xref:System.IAsyncResult> retornado do método **Begin***OperationName* da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="79a5b-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method.</span></span> <span data-ttu-id="79a5b-108">Para obter um exemplo que demonstra essa abordagem, consulte [Bloqueando a execução de um aplicativo com um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="79a5b-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="79a5b-109">Aplicativos que usam o método **End***OperationName* para bloquear até a conclusão de uma operação assíncrona normalmente chamam o método **Begin***OperationName*, executam qualquer trabalho que possa ser feito sem os resultados da operação e, em seguida, chamam **End***OperationName*.</span><span class="sxs-lookup"><span data-stu-id="79a5b-109">Applications that use the **End***OperationName* method to block until an asynchronous operation is complete will typically call the **Begin***OperationName* method, perform any work that can be done without the results of the operation, and then call **End***OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79a5b-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79a5b-110">Example</span></span>  
 <span data-ttu-id="79a5b-111">O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do Sistema de Nomes de Domínio de computadores especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="79a5b-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="79a5b-112">Observe que `null` (`Nothing` no Visual Basic) é passado para os parâmetros <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` e `stateObject` porque esses argumentos não são necessários ao usar essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="79a5b-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="79a5b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79a5b-113">See Also</span></span>  
 [<span data-ttu-id="79a5b-114">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="79a5b-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="79a5b-115">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="79a5b-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
