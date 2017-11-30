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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 596d2be26318b782423653b4eb3f43c1f9fc4b92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="c2ec7-102">Programação assíncrona usando delegados</span><span class="sxs-lookup"><span data-stu-id="c2ec7-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="c2ec7-103">Delegados permitem que você chamar um método síncrono de maneira assíncrona.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="c2ec7-104">Quando você chama um delegado de forma síncrona, o `Invoke` método chama o método de destino diretamente no thread atual.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="c2ec7-105">Se o `BeginInvoke` método é chamado, o common language runtime (CLR) as filas de solicitação e retorna imediatamente ao chamador.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="c2ec7-106">O método de destino é chamado de forma assíncrona em um thread do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="c2ec7-107">O thread original, que enviou a solicitação, é gratuito continuar a executar em paralelo com o método de destino.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="c2ec7-108">Se um método de retorno de chamada foi especificado na chamada para o `BeginInvoke` método, o método de retorno de chamada é chamado quando o método de destino termina.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="c2ec7-109">O método de retorno de chamada, o `EndInvoke` método obtém o valor de retorno e os parâmetros de entrada/saída ou somente de saída.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="c2ec7-110">Se nenhum método de retorno de chamada é especificado ao chamar `BeginInvoke`, `EndInvoke` pode ser chamado do thread que chamou `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2ec7-111">Compiladores emitirá classes delegate com `Invoke`, `BeginInvoke`, e `EndInvoke` métodos usando a assinatura do delegado especificada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="c2ec7-112">O `BeginInvoke` e `EndInvoke` métodos devem ser decorados como nativo.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="c2ec7-113">Como esses métodos são marcados como nativo, o CLR fornece automaticamente a implementação em tempo de carregamento de classe.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="c2ec7-114">O carregador garante que elas não são substituídas.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2ec7-115">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c2ec7-115">In This Section</span></span>  
 [<span data-ttu-id="c2ec7-116">Chamando métodos síncronos de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="c2ec7-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="c2ec7-117">Discute o uso de delegates para fazer chamadas para métodos comuns e fornece exemplos de código simples que mostram quatro maneiras para aguardar uma chamada assíncrona retornar.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c2ec7-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c2ec7-118">Related Sections</span></span>  
 [<span data-ttu-id="c2ec7-119">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="c2ec7-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="c2ec7-120">Descreve a programação assíncrona com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ec7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2ec7-121">See Also</span></span>  
 <xref:System.Delegate>
