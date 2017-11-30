---
title: "Usando um delegado AsyncCallback para finalizar uma operação assíncrona"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="6d154-102">Usando um delegado AsyncCallback para finalizar uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="6d154-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="6d154-103">Aplicativos que podem executar outras tarefas enquanto aguarda os resultados de uma operação assíncrona não devem bloquear a esperar até que a operação for concluída.</span><span class="sxs-lookup"><span data-stu-id="6d154-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="6d154-104">Use uma das opções a seguir para continuar a execução de instruções enquanto aguarda uma operação assíncrona concluir:</span><span class="sxs-lookup"><span data-stu-id="6d154-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="6d154-105">Use um <xref:System.AsyncCallback> delegado para processar os resultados da operação assíncrona em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="6d154-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="6d154-106">Essa abordagem é demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="6d154-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="6d154-107">Use o <xref:System.IAsyncResult.IsCompleted%2A> propriedade o <xref:System.IAsyncResult> retornado da operação assíncrona **começar** *OperationName* método para determinar se a operação foi concluída.</span><span class="sxs-lookup"><span data-stu-id="6d154-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="6d154-108">Para obter um exemplo que demonstra essa abordagem, consulte [sondagem do status de uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="6d154-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d154-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d154-109">Example</span></span>  
 <span data-ttu-id="6d154-110">O exemplo de código a seguir demonstra como usar métodos assíncronos no <xref:System.Net.Dns> classe para recuperar informações do sistema de nome de domínio (DNS) de computadores especificado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6d154-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="6d154-111">Este exemplo cria um <xref:System.AsyncCallback> representante que referencia o `ProcessDnsInformation` método.</span><span class="sxs-lookup"><span data-stu-id="6d154-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="6d154-112">Esse método é chamado uma vez para cada solicitação assíncrona para obter informações de DNS.</span><span class="sxs-lookup"><span data-stu-id="6d154-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="6d154-113">Observe que o host especificado pelo usuário é passado para o <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6d154-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="6d154-114">Para obter um exemplo que demonstra a definição e uso de um objeto de estado mais complexo, consulte [usando um delegado AsyncCallback e um objeto de estado](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="6d154-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6d154-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d154-115">See Also</span></span>  
 [<span data-ttu-id="6d154-116">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="6d154-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="6d154-117">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="6d154-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="6d154-118">Chamando métodos assíncronos usando IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="6d154-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="6d154-119">Usando um representante AsyncCallback e um objeto de estado</span><span class="sxs-lookup"><span data-stu-id="6d154-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
