---
title: Sondando o status de uma operação assíncrona
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1bf2b2c4fdacda2b44498ab8e1c98c8fa9c6d5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567387"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="98b23-102">Sondando o status de uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="98b23-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="98b23-103">Os aplicativos que podem executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona não devem bloquear a espera até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="98b23-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="98b23-104">Use uma das opções a seguir para continuar a execução das instruções ao aguardar a conclusão de uma operação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="98b23-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="98b23-105">Use a propriedade <xref:System.IAsyncResult.IsCompleted%2A> do <xref:System.IAsyncResult> retornado do método **Begin***OperationName* da operação assíncrona para determinar se a operação foi concluída.</span><span class="sxs-lookup"><span data-stu-id="98b23-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="98b23-106">Essa abordagem é conhecida como sondagem e será demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="98b23-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="98b23-107">Use um representante do <xref:System.AsyncCallback> para processar os resultados da operação assíncrona em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="98b23-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="98b23-108">Veja um exemplo que demonstra essa abordagem em [Usar um representante AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="98b23-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98b23-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98b23-109">Example</span></span>  
 <span data-ttu-id="98b23-110">O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do Sistema de Nomes de Domínio de computadores especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="98b23-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="98b23-111">Este exemplo inicia a operação assíncrona e, em seguida, imprime pontos (".") no console até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="98b23-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="98b23-112">Observe que **nulo** (**Nada** no Visual Basic) é passado para os parâmetros <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> e <xref:System.Object> porque esses argumentos não são necessários quando se usa essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="98b23-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="98b23-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98b23-113">See Also</span></span>  
 [<span data-ttu-id="98b23-114">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="98b23-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="98b23-115">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="98b23-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
