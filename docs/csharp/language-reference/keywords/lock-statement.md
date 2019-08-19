---
title: instrução lock – referência em C#
ms.custom: seodec18
description: Use a instrução lock do C# para sincronizar o acesso de thread com um recurso compartilhado
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 7ae19e48467bf5feca115c993c2299c1ecbaadc7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566338"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="5f79b-103">instrução lock (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="5f79b-103">lock statement (C# reference)</span></span>

<span data-ttu-id="5f79b-104">A instrução `lock` obtém o bloqueio de exclusão mútua para um determinado objeto, executa um bloco de instruções e, em seguida, libera o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5f79b-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="5f79b-105">Embora um bloqueio seja mantido, o thread que mantém o bloqueio pode adquiri-lo novamente e liberá-lo.</span><span class="sxs-lookup"><span data-stu-id="5f79b-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="5f79b-106">Qualquer outro thread é impedido de adquirir o bloqueio e aguarda até que ele seja liberado.</span><span class="sxs-lookup"><span data-stu-id="5f79b-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="5f79b-107">A instrução `lock` está no formato</span><span class="sxs-lookup"><span data-stu-id="5f79b-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="5f79b-108">em que `x` é uma expressão de um [tipo de referência](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="5f79b-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="5f79b-109">Ela é precisamente equivalente a</span><span class="sxs-lookup"><span data-stu-id="5f79b-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="5f79b-110">Como o código usa um bloco [try...finally](try-finally.md), o bloqueio será liberado mesmo se uma exceção for gerada dentro do corpo de uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="5f79b-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="5f79b-111">Não é possível usar a palavra-chave [await](await.md) no corpo de uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="5f79b-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f79b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f79b-112">Remarks</span></span>

<span data-ttu-id="5f79b-113">Ao sincronizar o acesso de thread com um recurso compartilhado, bloqueie uma instância de objeto dedicada (por exemplo, `private readonly object balanceLock = new object();`) ou outra instância que provavelmente não será usada como um objeto de bloqueio por partes não relacionadas do código.</span><span class="sxs-lookup"><span data-stu-id="5f79b-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="5f79b-114">Evite usar a mesma instância de objeto de bloqueio para diferentes recursos compartilhados, uma vez que ela poderia resultar em deadlock ou contenção de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5f79b-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="5f79b-115">Especificamente, evite usar os seguintes itens como objetos de bloqueio:</span><span class="sxs-lookup"><span data-stu-id="5f79b-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="5f79b-116">`this`, uma vez que pode ser usado pelos chamadores como um bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5f79b-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="5f79b-117">Instâncias <xref:System.Type>, pois podem ser obtidas pelo operador ou reflexão [typeof](../operators/type-testing-and-cast.md#typeof-operator).</span><span class="sxs-lookup"><span data-stu-id="5f79b-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="5f79b-118">Instâncias de cadeia de caracteres, incluindo literais de cadeia de caracteres, pois podem ser [internalizadas](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="5f79b-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="5f79b-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f79b-119">Example</span></span>

<span data-ttu-id="5f79b-120">O exemplo a seguir define uma classe `Account` que sincroniza o acesso com seu campo privado `balance` bloqueando uma instância `balanceLock` dedicada.</span><span class="sxs-lookup"><span data-stu-id="5f79b-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="5f79b-121">Usar a mesma instância para bloquear garante que o campo `balance` não pode ser atualizado simultaneamente por dois threads que tentam chamar os métodos `Debit` ou `Credit` simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="5f79b-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="5f79b-122">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5f79b-122">C# language specification</span></span>

<span data-ttu-id="5f79b-123">Para saber mais, confira a seção [A instrução lock](~/_csharplang/spec/statements.md#the-lock-statement) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5f79b-123">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f79b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f79b-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="5f79b-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5f79b-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5f79b-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="5f79b-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="5f79b-127">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="5f79b-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
