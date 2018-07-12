---
title: Bloqueando a execução de aplicativos com um AsyncWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a1f9c7a5c1e083500ccf88d7a165e109238e875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567319"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="50f05-102">Bloqueando a execução de aplicativos com um AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="50f05-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="50f05-103">Aplicativos que não continuem a executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="50f05-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="50f05-104">Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar a conclusão de uma operação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="50f05-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="50f05-105">Use a propriedade <xref:System.IAsyncResult.AsyncWaitHandle%2A> do <xref:System.IAsyncResult> retornado do método **Begin***OperationName* da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="50f05-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method.</span></span> <span data-ttu-id="50f05-106">Esta abordagem será demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="50f05-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="50f05-107">Chame o método **End***OperationName* de operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="50f05-107">Call the asynchronous operation's **End***OperationName* method.</span></span> <span data-ttu-id="50f05-108">Veja um exemplo que demonstra essa abordagem em [Bloqueando a execução de um aplicativo ao encerrar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="50f05-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="50f05-109">Aplicativos que usam um ou mais objetos <xref:System.Threading.WaitHandle> para bloquear até a conclusão de uma operação assíncrona, tipicamente chamam o método **Begin***OperationName*, executam qualquer trabalho que possa ser feito sem os resultados da operação e, em seguida, bloqueiam até a conclusão das operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="50f05-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin***OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="50f05-110">Um aplicativo pode bloquear em uma única operação ao chamar um dos métodos <xref:System.Threading.WaitHandle.WaitOne%2A> usando o <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span><span class="sxs-lookup"><span data-stu-id="50f05-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="50f05-111">Para bloquear enquanto espera a conclusão de um conjunto de operações assíncronas, armazene os objetos <xref:System.IAsyncResult.AsyncWaitHandle%2A> associados em uma matriz e chame um dos métodos <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="50f05-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="50f05-112">Para bloquear enquanto espera a conclusão de um conjunto de operações assíncronas, armazene os objetos <xref:System.IAsyncResult.AsyncWaitHandle%2A> associados em uma matriz e chame um dos métodos <xref:System.Threading.WaitHandle.WaitAny%2A>.</span><span class="sxs-lookup"><span data-stu-id="50f05-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50f05-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50f05-113">Example</span></span>  
 <span data-ttu-id="50f05-114">O exemplo de código a seguir demonstra como usar métodos assíncronos na classe DNS para recuperar informações do Sistema de Nomes de Domínio de computadores especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="50f05-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="50f05-115">O exemplo demonstra o bloqueio usando o <xref:System.Threading.WaitHandle> associado com a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="50f05-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="50f05-116">Observe que `null` (`Nothing` no Visual Basic) é passado para os parâmetros <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` e `stateObject` por não serem necessários ao usar essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="50f05-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="50f05-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50f05-117">See Also</span></span>  
 [<span data-ttu-id="50f05-118">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="50f05-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="50f05-119">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="50f05-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
