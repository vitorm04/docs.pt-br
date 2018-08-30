---
title: Instrução lock (referência em C#)
description: 'A palavra-chave lock é usada em threading '
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6ed46837482642dfd7e1a96cd120fc18023c5e9f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931187"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="ef6a0-103">Instrução lock (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="ef6a0-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="ef6a0-104">A palavra-chave `lock` marca um bloco de instruções como uma seção crítica obtendo o bloqueio de exclusão mútua para um determinado objeto, executando uma instrução e, em seguida, liberando o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-104">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="ef6a0-105">O exemplo a seguir inclui uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-105">The following example includes a `lock` statement.</span></span>

```csharp
class Account
{
    decimal balance;
    private Object thisLock = new Object();

    public void Withdraw(decimal amount)
    {
        lock (thisLock)
        {
            if (amount > balance)
            {
                throw new Exception("Insufficient funds");
            }
            balance -= amount;
        }
    }
}
```

<span data-ttu-id="ef6a0-106">Para obter mais informações, consulte [Sincronização de thread](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="ef6a0-106">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="ef6a0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef6a0-107">Remarks</span></span>

<span data-ttu-id="ef6a0-108">A palavra-chave `lock` garante que um thread não insere uma seção crítica do código enquanto outro thread está na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-108">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="ef6a0-109">Se outro thread tentar inserir um código bloqueado, ele aguardará, bloqueado, até que o objeto seja liberado.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-109">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>

<span data-ttu-id="ef6a0-110">A seção [Threading](../../programming-guide/concepts/threading/index.md) discute o threading.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-110">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>

<span data-ttu-id="ef6a0-111">A palavra-chave `lock` chama <xref:System.Threading.Monitor.Enter%2A> no início do bloco e <xref:System.Threading.Monitor.Exit%2A> no fim do bloco.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-111">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="ef6a0-112">Uma <xref:System.Threading.ThreadInterruptedException> será gerada se <xref:System.Threading.Thread.Interrupt%2A> interromper um thread que está esperando para inserir uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-112">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>

<span data-ttu-id="ef6a0-113">Em geral, evite o bloqueio em um tipo `public` ou instâncias além do controle do código.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-113">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="ef6a0-114">Os constructos comuns `lock (this)`, `lock (typeof (MyType))` e `lock ("myLock")` violam essa diretriz:</span><span class="sxs-lookup"><span data-stu-id="ef6a0-114">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>

- <span data-ttu-id="ef6a0-115">`lock (this)` é um problema se a instância pode ser acessada publicamente.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-115">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>

- <span data-ttu-id="ef6a0-116">`lock (typeof (MyType))` é um problema se `MyType` está acessível publicamente.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-116">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>

- <span data-ttu-id="ef6a0-117">`lock("myLock")` é um problema porque qualquer outro código no processo usando a mesma cadeia de caracteres compartilhará o mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-117">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>

<span data-ttu-id="ef6a0-118">A prática recomendada é definir um objeto `private` para bloquear ou uma variável de objeto `private static` para proteger dados comuns a todas as instâncias.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-118">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>

<span data-ttu-id="ef6a0-119">Não é possível usar a palavra-chave [await](await.md) no corpo de uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-119">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="example---threads-without-locking"></a><span data-ttu-id="ef6a0-120">Exemplo – threads sem bloqueio</span><span class="sxs-lookup"><span data-stu-id="ef6a0-120">Example - Threads without locking</span></span>

<span data-ttu-id="ef6a0-121">O exemplo a seguir mostra um uso simples de threads sem bloqueio em C#:</span><span class="sxs-lookup"><span data-stu-id="ef6a0-121">The following sample shows a simple use of threads without locking in C#:</span></span>

[!code-csharp[csrefKeywordsFixedLock#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#5)]

## <a name="example---threads-using-locking"></a><span data-ttu-id="ef6a0-122">Exemplo – Threads usando bloqueio</span><span class="sxs-lookup"><span data-stu-id="ef6a0-122">Example - Threads using locking</span></span>

<span data-ttu-id="ef6a0-123">O exemplo a seguir usa threads e `lock`.</span><span class="sxs-lookup"><span data-stu-id="ef6a0-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="ef6a0-124">Enquanto a instrução `lock` estiver presente, o bloco de instrução será uma seção crítica e `balance` nunca se tornará um número negativo:</span><span class="sxs-lookup"><span data-stu-id="ef6a0-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number:</span></span>

[!code-csharp[csrefKeywordsFixedLock#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="ef6a0-125">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ef6a0-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ef6a0-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef6a0-126">See also</span></span>

- <xref:System.Reflection.MethodImplAttributes>
- <xref:System.Threading.Mutex>
- <xref:System.Threading.Monitor>
- [<span data-ttu-id="ef6a0-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ef6a0-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="ef6a0-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ef6a0-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ef6a0-129">Threading</span><span class="sxs-lookup"><span data-stu-id="ef6a0-129">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
- [<span data-ttu-id="ef6a0-130">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="ef6a0-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ef6a0-131">Palavras-chave de instrução</span><span class="sxs-lookup"><span data-stu-id="ef6a0-131">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="ef6a0-132">Operações interconectadas</span><span class="sxs-lookup"><span data-stu-id="ef6a0-132">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)
- [<span data-ttu-id="ef6a0-133">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="ef6a0-133">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)
- [<span data-ttu-id="ef6a0-134">Sincronização de Thread </span><span class="sxs-lookup"><span data-stu-id="ef6a0-134">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)