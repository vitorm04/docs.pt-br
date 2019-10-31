---
title: Usando um delegado AsyncCallback e um objeto de estado
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094598"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="2f65c-102">Usando um delegado AsyncCallback e um objeto de estado</span><span class="sxs-lookup"><span data-stu-id="2f65c-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="2f65c-103">Ao usar um representante <xref:System.AsyncCallback> para processar os resultados da operação assíncrona em um thread separado, você pode usar um objeto de estado para passar informações entre os retornos de chamada e recuperar um resultado final.</span><span class="sxs-lookup"><span data-stu-id="2f65c-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="2f65c-104">Este tópico demonstra essa prática expandindo o exemplo em [Usando um representante AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2f65c-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f65c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f65c-105">Example</span></span>  
 <span data-ttu-id="2f65c-106">O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do DNS (Sistema de Nomes de Domínio) de computadores especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2f65c-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="2f65c-107">Este exemplo define e usa a classe `HostRequest` para armazenar informações de estado.</span><span class="sxs-lookup"><span data-stu-id="2f65c-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="2f65c-108">Um objeto `HostRequest` é criado para cada nome de computador inserido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2f65c-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="2f65c-109">Este objeto é passado para o método <xref:System.Net.Dns.BeginGetHostByName%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f65c-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="2f65c-110">O método `ProcessDnsInformation` é chamado sempre que uma solicitação é concluída.</span><span class="sxs-lookup"><span data-stu-id="2f65c-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="2f65c-111">O objeto `HostRequest` é recuperado usando a propriedade <xref:System.IAsyncResult.AsyncState%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f65c-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="2f65c-112">O método `ProcessDnsInformation` usa o objeto `HostRequest` para armazenar o retornado <xref:System.Net.IPHostEntry> pela solicitação ou um <xref:System.Net.Sockets.SocketException> lançado pela solicitação.</span><span class="sxs-lookup"><span data-stu-id="2f65c-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="2f65c-113">Quando todas as solicitações são concluídas, o aplicativo faz a iteração pelos objetos `HostRequest` e exibe as informações de DNS ou a mensagem de erro <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="2f65c-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2f65c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f65c-114">See also</span></span>

- [<span data-ttu-id="2f65c-115">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="2f65c-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="2f65c-116">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="2f65c-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="2f65c-117">Usando um representante AsyncCallback para finalizar uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="2f65c-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
