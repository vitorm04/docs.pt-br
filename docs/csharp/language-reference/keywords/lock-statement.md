---
title: Instrução lock (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960941"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="7ae15-102">Instrução lock (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7ae15-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="7ae15-103">A palavra-chave `lock` marca um bloco de instruções como uma seção crítica obtendo o bloqueio de exclusão mútua para um determinado objeto, executando uma instrução e, em seguida, liberando o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7ae15-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="7ae15-104">O exemplo a seguir inclui uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="7ae15-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="7ae15-105">Para obter mais informações, consulte [Sincronização de thread](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="7ae15-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ae15-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ae15-106">Remarks</span></span>  
 <span data-ttu-id="7ae15-107">A palavra-chave `lock` garante que um thread não insere uma seção crítica do código enquanto outro thread está na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="7ae15-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="7ae15-108">Se outro thread tentar inserir um código bloqueado, ele aguardará, bloqueado, até que o objeto seja liberado.</span><span class="sxs-lookup"><span data-stu-id="7ae15-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="7ae15-109">A seção [Threading](../../programming-guide/concepts/threading/index.md) discute o threading.</span><span class="sxs-lookup"><span data-stu-id="7ae15-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="7ae15-110">A palavra-chave `lock` chama <xref:System.Threading.Monitor.Enter%2A> no início do bloco e <xref:System.Threading.Monitor.Exit%2A> no fim do bloco.</span><span class="sxs-lookup"><span data-stu-id="7ae15-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="7ae15-111">Uma <xref:System.Threading.ThreadInterruptedException> será gerada se <xref:System.Threading.Thread.Interrupt%2A> interromper um thread que está esperando para inserir uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="7ae15-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="7ae15-112">Em geral, evite o bloqueio em um tipo `public` ou instâncias além do controle do código.</span><span class="sxs-lookup"><span data-stu-id="7ae15-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="7ae15-113">Os constructos comuns `lock (this)`, `lock (typeof (MyType))` e `lock ("myLock")` violam essa diretriz:</span><span class="sxs-lookup"><span data-stu-id="7ae15-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="7ae15-114">`lock (this)` é um problema se a instância pode ser acessada publicamente.</span><span class="sxs-lookup"><span data-stu-id="7ae15-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="7ae15-115">`lock (typeof (MyType))` é um problema se `MyType` está acessível publicamente.</span><span class="sxs-lookup"><span data-stu-id="7ae15-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="7ae15-116">`lock("myLock")` é um problema porque qualquer outro código no processo usando a mesma cadeia de caracteres compartilhará o mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7ae15-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="7ae15-117">A prática recomendada é definir um objeto `private` para bloquear ou uma variável de objeto `private static` para proteger dados comuns a todas as instâncias.</span><span class="sxs-lookup"><span data-stu-id="7ae15-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="7ae15-118">Não é possível usar a palavra-chave [await](../../../csharp/language-reference/keywords/await.md) no corpo de uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="7ae15-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ae15-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ae15-119">Example</span></span>  
 <span data-ttu-id="7ae15-120">O exemplo a seguir mostra um uso simples de threads sem bloqueio em C#.</span><span class="sxs-lookup"><span data-stu-id="7ae15-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="7ae15-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ae15-121">Example</span></span>  
 <span data-ttu-id="7ae15-122">O exemplo a seguir usa threads e `lock`.</span><span class="sxs-lookup"><span data-stu-id="7ae15-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="7ae15-123">Enquanto a instrução `lock` estiver presente, o bloco de instrução será uma seção crítica e `balance` nunca se tornará um número negativo.</span><span class="sxs-lookup"><span data-stu-id="7ae15-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7ae15-124">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7ae15-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ae15-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ae15-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="7ae15-126">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7ae15-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7ae15-127">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7ae15-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7ae15-128">Threading</span><span class="sxs-lookup"><span data-stu-id="7ae15-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="7ae15-129">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7ae15-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7ae15-130">Palavras-chave de instrução</span><span class="sxs-lookup"><span data-stu-id="7ae15-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="7ae15-131">Operações interconectadas</span><span class="sxs-lookup"><span data-stu-id="7ae15-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="7ae15-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="7ae15-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="7ae15-133">Sincronização de Thread </span><span class="sxs-lookup"><span data-stu-id="7ae15-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
