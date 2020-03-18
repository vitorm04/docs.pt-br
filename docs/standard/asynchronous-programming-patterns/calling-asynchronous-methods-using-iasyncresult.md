---
title: Chamando métodos assíncronos usando IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121307"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="e4141-102">Chamando métodos assíncronos usando IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="e4141-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="e4141-103">Tipos em bibliotecas de classes de terceiros e no .NET Framework podem fornecer métodos que permitem que um aplicativo continue a ser executado durante o desempenho de operações assíncronas em threads diferentes do thread principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4141-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="e4141-104">As seções a seguir descrevem e fornecem exemplos de código que demonstram diferentes maneiras de chamar métodos assíncronos que usam o padrão de design <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="e4141-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="e4141-105">[Bloqueando a execução do aplicativo terminando uma operação de sincronização](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e4141-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="e4141-106">[Bloqueando a execução do aplicativo usando um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="e4141-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="e4141-107">[Votação para o Status de uma Operação Assíncrona](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e4141-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="e4141-108">[Usando um Delegado AsyncCallback para acabar com uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e4141-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4141-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="e4141-109">See also</span></span>

- [<span data-ttu-id="e4141-110">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="e4141-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="e4141-111">Visão geral do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="e4141-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
