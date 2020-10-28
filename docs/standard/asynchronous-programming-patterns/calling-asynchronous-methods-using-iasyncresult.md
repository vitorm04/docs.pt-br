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
ms.openlocfilehash: 8e11f734410e266aa4c175551e8a3fbf5d9236c9
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888900"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="c7a67-102">Chamando métodos assíncronos usando IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="c7a67-102">Calling Asynchronous Methods Using IAsyncResult</span></span>

<span data-ttu-id="c7a67-103">Os tipos nas bibliotecas .NET e bibliotecas de classe de terceiros podem fornecer métodos que permitem que um aplicativo continue a execução enquanto executa operações assíncronas em threads diferentes do thread do aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="c7a67-103">Types in the .NET libraries and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="c7a67-104">As seções a seguir descrevem e fornecem exemplos de código que demonstram diferentes maneiras de chamar métodos assíncronos que usam o padrão de design <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="c7a67-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="c7a67-105">[Bloqueio da execução do aplicativo encerrando uma operação assíncrona](blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="c7a67-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="c7a67-106">[Bloqueando a execução do aplicativo usando um AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="c7a67-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="c7a67-107">[Sondando o status de uma operação assíncrona](polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="c7a67-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="c7a67-108">[Usando um delegado AsyncCallback para finalizar uma operação assíncrona](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="c7a67-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a67-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="c7a67-109">See also</span></span>

- [<span data-ttu-id="c7a67-110">Padrão assíncrono baseado em evento (EAP)</span><span class="sxs-lookup"><span data-stu-id="c7a67-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="c7a67-111">Visão geral do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="c7a67-111">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
