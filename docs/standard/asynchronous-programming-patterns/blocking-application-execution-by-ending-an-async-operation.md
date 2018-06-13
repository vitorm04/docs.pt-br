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
ms.openlocfilehash: db46025ca1169f2f93a5b8eabb62a06ccc4bb95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567413"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="807e7-102">Bloqueando a execução de um aplicativo finalizando uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="807e7-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="807e7-103">Aplicativos que não continuem a executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="807e7-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="807e7-104">Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar a conclusão de uma operação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="807e7-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="807e7-105">Chame o método **End***OperationName* de operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="807e7-105">Call the asynchronous operations **End***OperationName* method.</span></span> <span data-ttu-id="807e7-106">Esta abordagem será demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="807e7-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="807e7-107">Use a propriedade <xref:System.IAsyncResult.AsyncWaitHandle%2A> do <xref:System.IAsyncResult> retornado do método **Begin***OperationName* da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="807e7-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method.</span></span> <span data-ttu-id="807e7-108">Para obter um exemplo que demonstra essa abordagem, consulte [Bloqueando a execução de um aplicativo com um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="807e7-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="807e7-109">Aplicativos que usam o método **End***OperationName* para bloquear até a conclusão de uma operação assíncrona normalmente chamam o método **Begin***OperationName*, executam qualquer trabalho que possa ser feito sem os resultados da operação e, em seguida, chamam **End***OperationName*.</span><span class="sxs-lookup"><span data-stu-id="807e7-109">Applications that use the **End***OperationName* method to block until an asynchronous operation is complete will typically call the **Begin***OperationName* method, perform any work that can be done without the results of the operation, and then call **End***OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="807e7-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="807e7-110">Example</span></span>  
 <span data-ttu-id="807e7-111">O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do Sistema de Nomes de Domínio de computadores especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="807e7-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="807e7-112">Observe que `null` (`Nothing` no Visual Basic) é passado para os parâmetros <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` e `stateObject` porque esses argumentos não são necessários ao usar essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="807e7-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="807e7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="807e7-113">See Also</span></span>  
 [<span data-ttu-id="807e7-114">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="807e7-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="807e7-115">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="807e7-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
