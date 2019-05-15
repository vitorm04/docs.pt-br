---
title: Usando um delegado AsyncCallback para finalizar uma operação assíncrona
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e53634cea4ab3d260247ce645956c68ea7e2e80
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623534"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="bc4c0-102">Usando um delegado AsyncCallback para finalizar uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="bc4c0-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="bc4c0-103">Os aplicativos que podem executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona não devem bloquear a espera até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="bc4c0-104">Use uma das opções a seguir para continuar a execução das instruções ao aguardar a conclusão de uma operação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="bc4c0-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="bc4c0-105">Use um representante do <xref:System.AsyncCallback> para processar os resultados da operação assíncrona em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="bc4c0-106">Esta abordagem será demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="bc4c0-107">Use a propriedade <xref:System.IAsyncResult.IsCompleted%2A> do <xref:System.IAsyncResult> retornado do método **Begin**_OperationName_ da operação assíncrona para determinar se a operação foi concluída.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="bc4c0-108">Veja um exemplo que demonstra essa abordagem em [Sondagem do status de uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="bc4c0-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc4c0-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc4c0-109">Example</span></span>  
 <span data-ttu-id="bc4c0-110">O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do DNS (Sistema de Nomes de Domínio) de computadores especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="bc4c0-111">Este exemplo cria um representante <xref:System.AsyncCallback> que referencia o método `ProcessDnsInformation`.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="bc4c0-112">Esse método é chamado uma vez para cada solicitação assíncrona para obter informações de DNS.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="bc4c0-113">Observe que o host especificado pelo usuário é passado para o parâmetro <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="bc4c0-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="bc4c0-114">Para obter um exemplo que demonstra a definição e uso de um objeto de estado mais complexo, veja [Usar um representante AsyncCallback e um objeto de estado](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="bc4c0-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bc4c0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc4c0-115">See also</span></span>

- [<span data-ttu-id="bc4c0-116">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="bc4c0-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="bc4c0-117">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="bc4c0-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="bc4c0-118">Chamando métodos assíncronos usando IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="bc4c0-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="bc4c0-119">Usando um representante AsyncCallback e um objeto de estado</span><span class="sxs-lookup"><span data-stu-id="bc4c0-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
