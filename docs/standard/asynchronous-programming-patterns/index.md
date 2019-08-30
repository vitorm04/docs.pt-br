---
title: Padrões de programação assíncrona
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36798fabcd42cf7e04b0a6f288736503eecad88b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169120"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="e7260-102">Padrões de programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="e7260-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="e7260-103">O .NET fornece três padrões para a execução de operações assíncronas:</span><span class="sxs-lookup"><span data-stu-id="e7260-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="e7260-104">**TAP (padrão assíncrono baseado em tarefa)** , que usa um único método para representar o início e a conclusão de uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e7260-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="e7260-105">O TAP foi introduzido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e7260-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="e7260-106">**É a abordagem recomendada para a programação assíncrona no .NET.**</span><span class="sxs-lookup"><span data-stu-id="e7260-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="e7260-107">As palavras-chave [async](../../csharp/language-reference/keywords/async.md) e [await](../../csharp/language-reference/operators/await.md) no C# e os operadores [Async](../../visual-basic/language-reference/modifiers/async.md) e [Await](../../visual-basic/language-reference/operators/await-operator.md) no Visual Basic adicionam suporte à linguagem para TAP.</span><span class="sxs-lookup"><span data-stu-id="e7260-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="e7260-108">Para saber mais, confira [Padrão assíncrono baseado em tarefa (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="e7260-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="e7260-109">**Padrão assíncrono baseado em evento (EAP)** , que é o modelo herdado baseado em evento para fornecimento do comportamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e7260-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="e7260-110">Ele requer um método que tem o sufixo `Async` e um ou mais eventos, tipos delegados de manipulador de eventos e tipos derivados de `EventArg`.</span><span class="sxs-lookup"><span data-stu-id="e7260-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="e7260-111">O EAP foi introduzido no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="e7260-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="e7260-112">Não é mais recomendado para novo desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e7260-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="e7260-113">Para saber mais, confira [EAP (Padrão Assíncrono baseado em Evento)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="e7260-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="e7260-114">Padrão de **Modelo de programação assíncrona (APM)** (também chamado de padrão <xref:System.IAsyncResult>), que é o modelo herdado que usa a interface <xref:System.IAsyncResult> para fornecimento do comportamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e7260-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="e7260-115">Nesse padrão, as operações síncronas exigem os métodos `Begin` e `End` (por exemplo, `BeginWrite` e `EndWrite` para implementar uma operação de gravação assíncrona).</span><span class="sxs-lookup"><span data-stu-id="e7260-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="e7260-116">Esse padrão não é mais recomendado para implantação nova.</span><span class="sxs-lookup"><span data-stu-id="e7260-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="e7260-117">Para saber mais, veja [APM (Modelo Assíncrono de Programação)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="e7260-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="e7260-118">Comparação de padrões</span><span class="sxs-lookup"><span data-stu-id="e7260-118">Comparison of patterns</span></span>

<span data-ttu-id="e7260-119">Para obter uma comparação rápida de como os três padrões modelam as operações assíncronas, considere um método `Read` que lê uma quantidade especificada de dados em um buffer fornecido começando em um deslocamento especificado:</span><span class="sxs-lookup"><span data-stu-id="e7260-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="e7260-120">O equivalente do TAP para este método poderia expor o método único `ReadAsync` a seguir:</span><span class="sxs-lookup"><span data-stu-id="e7260-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="e7260-121">O equivalente do EAP poderia expor o seguinte conjunto de tipos e membros:</span><span class="sxs-lookup"><span data-stu-id="e7260-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="e7260-122">O equivalente do APM poderia expor os métodos `BeginRead` e `EndRead`:</span><span class="sxs-lookup"><span data-stu-id="e7260-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="e7260-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7260-123">See also</span></span>

- [<span data-ttu-id="e7260-124">Assincronia detalhada</span><span class="sxs-lookup"><span data-stu-id="e7260-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="e7260-125">Programação assíncrona em C#</span><span class="sxs-lookup"><span data-stu-id="e7260-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="e7260-126">Programação assíncrona em F#</span><span class="sxs-lookup"><span data-stu-id="e7260-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="e7260-127">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7260-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
