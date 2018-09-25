---
title: Instrução lock (referência em C#)
description: Use a instrução lock C# para sincronizar o acesso de thread com o recurso compartilhado
ms.date: 08/28/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2b6fbfb2f81d7745c4effb9ea0087f34cc872a6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858350"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="e5a00-103">Instrução lock (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="e5a00-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="e5a00-104">A instrução `lock` obtém o bloqueio de exclusão mútua para um determinado objeto, executa um bloco de instruções, em seguida, libera o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e5a00-104">The `lock` statement obtains the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="e5a00-105">Embora um bloqueio seja mantido, o thread que mantém o bloqueio pode obtê-lo novamente e liberá-lo.</span><span class="sxs-lookup"><span data-stu-id="e5a00-105">While a lock is held, the thread that holds the lock can again obtain and release the lock.</span></span> <span data-ttu-id="e5a00-106">Qualquer outro thread é impedido de obter o bloqueio e aguarda até que ele seja liberado.</span><span class="sxs-lookup"><span data-stu-id="e5a00-106">Any other thread is blocked from obtaining the lock and waits until the lock is released.</span></span>

<span data-ttu-id="e5a00-107">A instrução `lock` está no formato</span><span class="sxs-lookup"><span data-stu-id="e5a00-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="e5a00-108">em que `x` é uma expressão de um [tipo de referência](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e5a00-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="e5a00-109">Ela é precisamente equivalente a</span><span class="sxs-lookup"><span data-stu-id="e5a00-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="e5a00-110">Como o código usa um bloco [try...finally](try-finally.md), o bloqueio será liberado mesmo se uma exceção for gerada dentro do corpo de uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="e5a00-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="e5a00-111">Não é possível usar a palavra-chave [await](await.md) no corpo de uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="e5a00-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5a00-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5a00-112">Remarks</span></span>

<span data-ttu-id="e5a00-113">Quando você sincroniza o acesso de thread com o recurso compartilhado, bloqueie uma instância de objeto dedicada (por exemplo, `private readonly object balanceLock = new object();`) ou outra instância que provavelmente não será usada como um objeto de bloqueio por partes não relacionadas do código.</span><span class="sxs-lookup"><span data-stu-id="e5a00-113">When you synchronize thread access to shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="e5a00-114">Evite usar a mesma instância de objeto de bloqueio para diferentes recursos compartilhados, uma vez que ela poderia resultar em deadlock ou contenção de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e5a00-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="e5a00-115">Em particular, evite usar</span><span class="sxs-lookup"><span data-stu-id="e5a00-115">In particular, avoid using</span></span>

- <span data-ttu-id="e5a00-116">`this` (pode ser usado pelos chamadores como um bloqueio),</span><span class="sxs-lookup"><span data-stu-id="e5a00-116">`this` (might be used by the callers as a lock),</span></span>
- <span data-ttu-id="e5a00-117"><xref:System.Type> instâncias (podem ser obtidas por meio do operador ou reflexão [typeof](typeof.md)),</span><span class="sxs-lookup"><span data-stu-id="e5a00-117"><xref:System.Type> instances (might be obtained by the [typeof](typeof.md) operator or reflection),</span></span>
- <span data-ttu-id="e5a00-118">instâncias de cadeia de caracteres, incluindo literais de cadeia de caracteres,</span><span class="sxs-lookup"><span data-stu-id="e5a00-118">string instances, including string literals,</span></span>

<span data-ttu-id="e5a00-119">como objetos de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e5a00-119">as lock objects.</span></span>

## <a name="example"></a><span data-ttu-id="e5a00-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5a00-120">Example</span></span>

<span data-ttu-id="e5a00-121">O exemplo a seguir define uma classe `Account` que sincroniza o acesso com seu campo privado `balance` bloqueando uma instância `balanceLock` dedicada.</span><span class="sxs-lookup"><span data-stu-id="e5a00-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="e5a00-122">Usar a mesma instância para bloquear garante que o campo `balance` não pode ser atualizado simultaneamente por dois threads que tentam chamar os métodos `Debit` ou `Credit` simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e5a00-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="e5a00-123">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e5a00-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e5a00-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5a00-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="e5a00-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e5a00-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e5a00-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e5a00-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e5a00-127">Palavras-chave de instrução</span><span class="sxs-lookup"><span data-stu-id="e5a00-127">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="e5a00-128">Operações interconectadas</span><span class="sxs-lookup"><span data-stu-id="e5a00-128">Interlocked operations</span></span>](../../../standard/threading/interlocked-operations.md)
- [<span data-ttu-id="e5a00-129">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="e5a00-129">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)