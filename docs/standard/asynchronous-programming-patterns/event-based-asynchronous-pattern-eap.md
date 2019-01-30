---
title: Padrão assíncrono baseado em evento (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 052773c615bcc4ddb5b735ae8164d44ed70bd935
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513484"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="69c2a-102">Padrão assíncrono baseado em evento (EAP)</span><span class="sxs-lookup"><span data-stu-id="69c2a-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="69c2a-103">Há várias maneiras de expor recursos assíncronos para o código cliente.</span><span class="sxs-lookup"><span data-stu-id="69c2a-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="69c2a-104">O Padrão Assíncrono baseado em evento prescreve uma maneira de as classes apresentarem comportamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="69c2a-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69c2a-105">A partir do .NET Framework 4, a Biblioteca de Paralelismo de Tarefas fornece um novo modelo de programação paralela e assíncrona.</span><span class="sxs-lookup"><span data-stu-id="69c2a-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="69c2a-106">Para obter mais informações, veja [Biblioteca de tarefas paralelas (TPL)](../parallel-programming/task-parallel-library-tpl.md) e [Padrão assíncrono baseado em tarefa (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="69c2a-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="69c2a-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="69c2a-107">In This Section</span></span>

 [<span data-ttu-id="69c2a-108">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="69c2a-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="69c2a-109">Descreve como o Padrão Assíncrono Baseado em Evento disponibiliza as vantagens de aplicativos de vários threads enquanto oculta muitos problemas complexos inerentes ao design com vários threads.</span><span class="sxs-lookup"><span data-stu-id="69c2a-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="69c2a-110">Implementando o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="69c2a-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="69c2a-111">Descreve a maneira padronizada de empacotar uma classe com recursos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="69c2a-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="69c2a-112">Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="69c2a-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="69c2a-113">Descreve as exigências para expor recursos assíncronos de acordo com o Padrão Assíncrono Baseado em Evento.</span><span class="sxs-lookup"><span data-stu-id="69c2a-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="69c2a-114">Decidindo quando implementar o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="69c2a-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="69c2a-115">Descreve como determinar quando você deve optar por implementar o Padrão assíncrono baseado em evento, em vez do padrão <xref:System.IAsyncResult> representado pelo [APM (Modelo de programação assíncrona)](asynchronous-programming-model-apm.md)</span><span class="sxs-lookup"><span data-stu-id="69c2a-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="69c2a-116">Como: implementar um componente compatível com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="69c2a-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="69c2a-117">Descreve como criar um componente que implemente o Padrão assíncrono baseado em evento.</span><span class="sxs-lookup"><span data-stu-id="69c2a-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="69c2a-118">É implementado usando classes do auxiliar do namespace <xref:System.ComponentModel?displayProperty=nameWithType>, o que garante que o componente funcione corretamente em qualquer modelo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69c2a-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="69c2a-119">Como: Implementar um cliente do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="69c2a-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="69c2a-120">Descreve como criar um cliente que usa um componente que implemente o Padrão assíncrono baseado em evento.</span><span class="sxs-lookup"><span data-stu-id="69c2a-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="69c2a-121">Como: usar componentes compatíveis com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="69c2a-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="69c2a-122">Descreve como usar um componente com suporte ao Padrão Assíncrono Baseado em Evento.</span><span class="sxs-lookup"><span data-stu-id="69c2a-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="69c2a-123">Referência</span><span class="sxs-lookup"><span data-stu-id="69c2a-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="69c2a-124">Descreve a classe <xref:System.ComponentModel.AsyncOperation> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="69c2a-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="69c2a-125">Descreve a classe <xref:System.ComponentModel.AsyncOperationManager> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="69c2a-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="69c2a-126">Descreve o componente <xref:System.ComponentModel.BackgroundWorker> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="69c2a-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="69c2a-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="69c2a-127">Related Sections</span></span>

 [<span data-ttu-id="69c2a-128">TPL (Biblioteca de Paralelismo de Tarefas)</span><span class="sxs-lookup"><span data-stu-id="69c2a-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="69c2a-129">Descreve um modelo de programação para operações paralelas e assíncronas.</span><span class="sxs-lookup"><span data-stu-id="69c2a-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="69c2a-130">Threading</span><span class="sxs-lookup"><span data-stu-id="69c2a-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="69c2a-131">Descreve recursos de multithreading no .NET.</span><span class="sxs-lookup"><span data-stu-id="69c2a-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c2a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69c2a-132">See also</span></span>

- [<span data-ttu-id="69c2a-133">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="69c2a-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="69c2a-134">Eventos</span><span class="sxs-lookup"><span data-stu-id="69c2a-134">Events</span></span>](../events/index.md)
- [<span data-ttu-id="69c2a-135">Padrões de design de programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="69c2a-135">Asynchronous Programming Design Patterns</span></span>](index.md)
