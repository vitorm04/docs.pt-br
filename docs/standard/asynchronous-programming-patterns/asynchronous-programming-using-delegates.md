---
title: "Programação assíncrona usando delegados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e84c004c8efc58c6d6ad55674470bec13fc0bab8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="9b37e-102">Programação assíncrona usando delegados</span><span class="sxs-lookup"><span data-stu-id="9b37e-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="9b37e-103">Os representantes permitem que você chame um método síncrono de maneira assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9b37e-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="9b37e-104">Quando você chama um representante de forma síncrona, o método `Invoke` chama o método de destino diretamente no thread atual.</span><span class="sxs-lookup"><span data-stu-id="9b37e-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="9b37e-105">Se o método `BeginInvoke` for chamado, o CLR (Common Language Runtime) enfileira a solicitação e retorna imediatamente ao chamador.</span><span class="sxs-lookup"><span data-stu-id="9b37e-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="9b37e-106">O método de destino é chamado de forma assíncrona em um thread a partir do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="9b37e-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="9b37e-107">O thread original, que enviou a solicitação, permanece livre para continuar a executar em paralelo com o método de destino.</span><span class="sxs-lookup"><span data-stu-id="9b37e-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="9b37e-108">Se um método de retorno de chamada foi especificado na chamada para o método `BeginInvoke`, o método de retorno de chamada é chamado quando termina o método de destino.</span><span class="sxs-lookup"><span data-stu-id="9b37e-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="9b37e-109">O método de retorno de chamada, o método `EndInvoke` obtém o valor retornado e os parâmetros de entrada/saída ou somente de saída.</span><span class="sxs-lookup"><span data-stu-id="9b37e-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="9b37e-110">Se nenhum método de retorno de chamada for especificado ao chamar `BeginInvoke`, `EndInvoke` pode ser chamado do thread que chamou `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="9b37e-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b37e-111">Os compiladores devem emitir classes de representante com os métodos `Invoke`, `BeginInvoke` e `EndInvoke` usando a assinatura de representante especificada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9b37e-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="9b37e-112">Os métodos `BeginInvoke` e `EndInvoke` devem ser decorados como nativos.</span><span class="sxs-lookup"><span data-stu-id="9b37e-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="9b37e-113">Como esses métodos são marcados como nativos, o CLR fornece automaticamente a implementação no tempo de carregamento da classe.</span><span class="sxs-lookup"><span data-stu-id="9b37e-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="9b37e-114">O carregador garante que eles não sejam substituídos.</span><span class="sxs-lookup"><span data-stu-id="9b37e-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b37e-115">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9b37e-115">In This Section</span></span>  
 [<span data-ttu-id="9b37e-116">Chamando métodos síncronos de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="9b37e-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="9b37e-117">Discute o uso de representantes para fazer chamadas assíncronas a métodos comuns e fornece exemplos de código simples que mostram quatro maneiras de aguardar o retorno de uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9b37e-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b37e-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9b37e-118">Related Sections</span></span>  
 [<span data-ttu-id="9b37e-119">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="9b37e-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="9b37e-120">Descreve a programação assíncrona com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b37e-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b37e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b37e-121">See Also</span></span>  
 <xref:System.Delegate>
