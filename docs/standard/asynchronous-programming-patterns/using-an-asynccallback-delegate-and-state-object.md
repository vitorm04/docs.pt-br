---
title: Usando um delegado AsyncCallback e um objeto de estado
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
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="75a08-102">Usando um delegado AsyncCallback e um objeto de estado</span><span class="sxs-lookup"><span data-stu-id="75a08-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="75a08-103">Quando você usa um <xref:System.AsyncCallback> delegar para processar os resultados da operação assíncrona em um thread separado, você pode usar um objeto de estado para transmitir informações entre os retornos de chamada e recuperar o resultado final.</span><span class="sxs-lookup"><span data-stu-id="75a08-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="75a08-104">Este tópico demonstra essa prática expandindo o exemplo [usando um delegado AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="75a08-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a08-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="75a08-105">Example</span></span>  
 <span data-ttu-id="75a08-106">O exemplo de código a seguir demonstra como usar métodos assíncronos no <xref:System.Net.Dns> classe para recuperar informações do sistema de nome de domínio (DNS) de computadores especificado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="75a08-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="75a08-107">Este exemplo define e usa o `HostRequest` classe para armazenar informações de estado.</span><span class="sxs-lookup"><span data-stu-id="75a08-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="75a08-108">Um `HostRequest` objeto é criado para cada nome de computador inserido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="75a08-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="75a08-109">Este objeto é passado para o <xref:System.Net.Dns.BeginGetHostByName%2A> método.</span><span class="sxs-lookup"><span data-stu-id="75a08-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="75a08-110">O `ProcessDnsInformation` método é chamado sempre que uma solicitação é concluída.</span><span class="sxs-lookup"><span data-stu-id="75a08-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="75a08-111">O `HostRequest` objeto é recuperado usando o <xref:System.IAsyncResult.AsyncState%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="75a08-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="75a08-112">O `ProcessDnsInformation` método usa o `HostRequest` objeto para armazenar o <xref:System.Net.IPHostEntry> retornado pela solicitação ou um <xref:System.Net.Sockets.SocketException> gerada pela solicitação.</span><span class="sxs-lookup"><span data-stu-id="75a08-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="75a08-113">Quando todas as solicitações estiverem concluídas, o aplicativo itera através de `HostRequest` objetos e exibe as informações de DNS ou <xref:System.Net.Sockets.SocketException> mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="75a08-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="75a08-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75a08-114">See Also</span></span>  
 [<span data-ttu-id="75a08-115">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="75a08-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="75a08-116">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="75a08-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="75a08-117">Usando um representante AsyncCallback para finalizar uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="75a08-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
