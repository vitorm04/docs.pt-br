---
title: Programação multithreaded com o padrão assíncrono baseado em evento
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
ms.openlocfilehash: 26e555a158ced352c297952b56f7557cbd825cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567296"
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a><span data-ttu-id="640c2-102">Programação multithreaded com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="640c2-102">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="640c2-103">Há várias maneiras de expor recursos assíncronos para o código cliente.</span><span class="sxs-lookup"><span data-stu-id="640c2-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="640c2-104">O Padrão Assíncrono Baseado em Evento prescreve a maneira recomendada de as classes apresentarem comportamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="640c2-104">The Event-based Asynchronous Pattern prescribes the recommended way for classes to present asynchronous behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="640c2-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="640c2-105">In This Section</span></span>  
 [<span data-ttu-id="640c2-106">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="640c2-106">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="640c2-107">Descreve como o Padrão Assíncrono Baseado em Evento disponibiliza as vantagens de aplicativos de vários threads enquanto oculta muitos problemas complexos inerentes ao design com vários threads.</span><span class="sxs-lookup"><span data-stu-id="640c2-107">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="640c2-108">Implementando o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="640c2-108">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="640c2-109">Descreve a maneira padronizada de empacotar uma classe com recursos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="640c2-109">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="640c2-110">Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="640c2-110">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="640c2-111">Descreve as exigências para expor recursos assíncronos de acordo com o Padrão Assíncrono Baseado em Evento.</span><span class="sxs-lookup"><span data-stu-id="640c2-111">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="640c2-112">Decidindo quando implementar o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="640c2-112">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="640c2-113">Descreve como determinar quando você deve escolher implementar o Padrão Assíncrono Baseado em Evento, em vez do padrão <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="640c2-113">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="640c2-114">Instruções passo a passo: implementando um componente compatível com o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="640c2-114">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="640c2-115">Ilustra como criar um componente que implemente o Padrão Assíncrono Baseado em Evento.</span><span class="sxs-lookup"><span data-stu-id="640c2-115">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="640c2-116">É implementado usando classes do auxiliar do namespace <xref:System.ComponentModel?displayProperty=nameWithType>, o que garante que o componente funcione corretamente em qualquer modelo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="640c2-116">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="640c2-117">Como usar componentes compatíveis com o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="640c2-117">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="640c2-118">Descreve como usar um componente com suporte ao Padrão Assíncrono Baseado em Evento.</span><span class="sxs-lookup"><span data-stu-id="640c2-118">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="640c2-119">Referência</span><span class="sxs-lookup"><span data-stu-id="640c2-119">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="640c2-120">Descreve a classe <xref:System.ComponentModel.AsyncOperation> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="640c2-120">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="640c2-121">Descreve a classe <xref:System.ComponentModel.AsyncOperationManager> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="640c2-121">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="640c2-122">Descreve o componente <xref:System.ComponentModel.BackgroundWorker> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="640c2-122">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640c2-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="640c2-123">See Also</span></span>  
 [<span data-ttu-id="640c2-124">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="640c2-124">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="640c2-125">Eventos</span><span class="sxs-lookup"><span data-stu-id="640c2-125">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="640c2-126">Multithreading em componentes</span><span class="sxs-lookup"><span data-stu-id="640c2-126">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="640c2-127">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="640c2-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
