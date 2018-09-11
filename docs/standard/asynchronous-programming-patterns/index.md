---
title: Padrões de programação assíncrona
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249030"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="0fc49-102">Padrões de programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="0fc49-102">Asynchronous Programming Patterns</span></span>

<span data-ttu-id="0fc49-103">O .NET Framework fornece três padrões para executar operações assíncronas:</span><span class="sxs-lookup"><span data-stu-id="0fc49-103">The .NET Framework provides three patterns for performing asynchronous operations:</span></span>  
  
- <span data-ttu-id="0fc49-104">**Padrão do APM (modelo de programação assíncrono)** (também chamado de padrão <xref:System.IAsyncResult>), em que operações assíncronas requerem os métodos `Begin` e `End` (por exemplo, `BeginWrite` e `EndWrite` para operações de gravação assíncronas).</span><span class="sxs-lookup"><span data-stu-id="0fc49-104">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), where asynchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` for asynchronous write operations).</span></span> <span data-ttu-id="0fc49-105">Esse padrão não é mais recomendado para implantação nova.</span><span class="sxs-lookup"><span data-stu-id="0fc49-105">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="0fc49-106">Para saber mais, veja [APM (Modelo Assíncrono de Programação)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="0fc49-106">For more information, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span></span>  
  
- <span data-ttu-id="0fc49-107">**EAP (padrão assíncrono baseado em eventos)**, que requer um método que tenha o sufixo `Async` e também requer um ou mais eventos, tipos de delegado do manipulador de eventos e tipos derivados de `EventArg`.</span><span class="sxs-lookup"><span data-stu-id="0fc49-107">**Event-based Asynchronous Pattern (EAP)**, which requires a method that has the `Async` suffix, and also requires one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="0fc49-108">O EAP foi introduzido no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="0fc49-108">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="0fc49-109">Ele não é mais recomendável para implantação nova.</span><span class="sxs-lookup"><span data-stu-id="0fc49-109">It is no longer recommended for new development.</span></span> <span data-ttu-id="0fc49-110">Para saber mais, confira [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="0fc49-110">For more information, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
- <span data-ttu-id="0fc49-111">**TAP (padrão assíncrono baseado em tarefa)**, que usa um único método para representar o início e a conclusão de uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="0fc49-111">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="0fc49-112">O TAP foi introduzido no .NET Framework 4 e é a abordagem recomendada para programação assíncrona no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fc49-112">TAP was introduced in the .NET Framework 4 and is the recommended approach to asynchronous programming in the .NET Framework.</span></span> <span data-ttu-id="0fc49-113">As palavras-chave [async](~/docs/csharp/language-reference/keywords/async.md) e [await](~/docs/csharp/language-reference/keywords/await.md) no #C e os operadores [Async](~/docs/visual-basic/language-reference/modifiers/async.md) e [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) no Visual Basic Language adicionam suporte à linguagem para TAP.</span><span class="sxs-lookup"><span data-stu-id="0fc49-113">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic Language add language support for TAP.</span></span> <span data-ttu-id="0fc49-114">Para saber mais, confira [Padrão assíncrono baseado em tarefa (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="0fc49-114">For more information, see [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>  
  
## <a name="comparing-patterns"></a><span data-ttu-id="0fc49-115">Comparando padrões</span><span class="sxs-lookup"><span data-stu-id="0fc49-115">Comparing Patterns</span></span>  

<span data-ttu-id="0fc49-116">Para obter uma comparação rápida de como os três padrões modelam as operações assíncronas, considere um método `Read` que lê uma quantidade especificada de dados em um buffer fornecido começando em um deslocamento especificado:</span><span class="sxs-lookup"><span data-stu-id="0fc49-116">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="0fc49-117">O equivalente do APM desse método poderia expor os métodos `BeginRead` e `EndRead`:</span><span class="sxs-lookup"><span data-stu-id="0fc49-117">The APM counterpart of this method would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
<span data-ttu-id="0fc49-118">O equivalente do EAP poderia expor o seguinte conjunto de tipos e membros:</span><span class="sxs-lookup"><span data-stu-id="0fc49-118">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="0fc49-119">O equivalente do TAP poderia expor o único método `ReadAsync` a seguir:</span><span class="sxs-lookup"><span data-stu-id="0fc49-119">The TAP counterpart would expose the following single `ReadAsync` method:</span></span>  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="0fc49-120">Para obter uma discussão abrangente de TAP, APM e EAP, consulte os links fornecidos na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="0fc49-120">For a comprehensive discussion of TAP, APM, and EAP, see the links provided in the next section.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="0fc49-121">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="0fc49-121">Related topics</span></span>

| <span data-ttu-id="0fc49-122">Título</span><span class="sxs-lookup"><span data-stu-id="0fc49-122">Title</span></span> | <span data-ttu-id="0fc49-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fc49-123">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="0fc49-124">APM (Modelo Assíncrono de Programação)</span><span class="sxs-lookup"><span data-stu-id="0fc49-124">Asynchronous Programming Model (APM)</span></span>](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | <span data-ttu-id="0fc49-125">Descreve o modelo herdado que usa a interface <xref:System.IAsyncResult> para fornecer comportamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="0fc49-125">Describes the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="0fc49-126">Esse modelo não é mais recomendado para implantação nova.</span><span class="sxs-lookup"><span data-stu-id="0fc49-126">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="0fc49-127">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="0fc49-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | <span data-ttu-id="0fc49-128">Descreve o modelo herdado baseado em eventos para fornecer comportamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="0fc49-128">Describes the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="0fc49-129">Esse modelo não é mais recomendado para implantação nova.</span><span class="sxs-lookup"><span data-stu-id="0fc49-129">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="0fc49-130">TAP (Padrão Assíncrono Baseado em Tarefa)</span><span class="sxs-lookup"><span data-stu-id="0fc49-130">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | <span data-ttu-id="0fc49-131">Descreve o novo padrão assíncrono baseado no namespace <xref:System.Threading.Tasks>.</span><span class="sxs-lookup"><span data-stu-id="0fc49-131">Describes the new asynchronous pattern based on the <xref:System.Threading.Tasks> namespace.</span></span> <span data-ttu-id="0fc49-132">Esse modelo é a abordagem recomendada para programação assíncrona no .NET Framework 4 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="0fc49-132">This model is the recommended approach to asynchronous programming in the .NET Framework 4 and later versions.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0fc49-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fc49-133">See also</span></span>

- [<span data-ttu-id="0fc49-134">Programação assíncrona em C#</span><span class="sxs-lookup"><span data-stu-id="0fc49-134">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)   
- [<span data-ttu-id="0fc49-135">Programação assíncrona em F#</span><span class="sxs-lookup"><span data-stu-id="0fc49-135">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [<span data-ttu-id="0fc49-136">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fc49-136">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
