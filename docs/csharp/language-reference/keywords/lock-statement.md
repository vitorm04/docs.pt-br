---
title: "Instrução lock (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
dev_langs:
- CSharp
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00dcbb9feec11587265bf61667d91c2c1598065b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="b1f91-102">Instrução lock (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b1f91-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="b1f91-103">A palavra-chave `lock` marca um bloco de instruções como uma seção crítica obtendo o bloqueio de exclusão mútua para um determinado objeto, executando uma instrução e, em seguida, liberando o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b1f91-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="b1f91-104">O exemplo a seguir inclui uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="b1f91-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="b1f91-105">Para obter mais informações, consulte [Sincronização de thread](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).</span><span class="sxs-lookup"><span data-stu-id="b1f91-105">For more information, see [Thread Synchronization](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1f91-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1f91-106">Remarks</span></span>  
 <span data-ttu-id="b1f91-107">A palavra-chave `lock` garante que um thread não insere uma seção crítica do código enquanto outro thread está na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="b1f91-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="b1f91-108">Se outro thread tentar inserir um código bloqueado, ele aguardará, bloqueado, até que o objeto seja liberado.</span><span class="sxs-lookup"><span data-stu-id="b1f91-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="b1f91-109">A seção [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) discute o threading.</span><span class="sxs-lookup"><span data-stu-id="b1f91-109">The section [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) discusses threading.</span></span>  
  
 <span data-ttu-id="b1f91-110">A palavra-chave `lock` chama <xref:System.Threading.Monitor.Enter%2A> no início do bloco e <xref:System.Threading.Monitor.Exit%2A> no fim do bloco.</span><span class="sxs-lookup"><span data-stu-id="b1f91-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="b1f91-111">Uma <xref:System.Threading.ThreadInterruptedException> será gerada se <xref:System.Threading.Thread.Interrupt%2A> interromper um thread que está esperando para inserir uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="b1f91-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="b1f91-112">Em geral, evite o bloqueio em um tipo `public` ou instâncias além do controle do código.</span><span class="sxs-lookup"><span data-stu-id="b1f91-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="b1f91-113">Os constructos comuns `lock (this)`, `lock (typeof (MyType))` e `lock ("myLock")` violam essa diretriz:</span><span class="sxs-lookup"><span data-stu-id="b1f91-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="b1f91-114">`lock (this)` é um problema se a instância pode ser acessada publicamente.</span><span class="sxs-lookup"><span data-stu-id="b1f91-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="b1f91-115">`lock (typeof (MyType))` é um problema se `MyType` está acessível publicamente.</span><span class="sxs-lookup"><span data-stu-id="b1f91-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="b1f91-116">`lock("myLock")` é um problema porque qualquer outro código no processo usando a mesma cadeia de caracteres compartilhará o mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b1f91-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="b1f91-117">A prática recomendada é definir um objeto `private` para bloquear ou uma variável de objeto `private static` para proteger dados comuns a todas as instâncias.</span><span class="sxs-lookup"><span data-stu-id="b1f91-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="b1f91-118">Não é possível usar a palavra-chave [await](../../../csharp/language-reference/keywords/await.md) no corpo de uma instrução `lock`.</span><span class="sxs-lookup"><span data-stu-id="b1f91-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1f91-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1f91-119">Example</span></span>  
 <span data-ttu-id="b1f91-120">O exemplo a seguir mostra um uso simples de threads sem bloqueio em C#.</span><span class="sxs-lookup"><span data-stu-id="b1f91-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 <span data-ttu-id="b1f91-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1f91-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1f91-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1f91-122">Example</span></span>  
 <span data-ttu-id="b1f91-123">O exemplo a seguir usa threads e `lock`.</span><span class="sxs-lookup"><span data-stu-id="b1f91-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="b1f91-124">Enquanto a instrução `lock` estiver presente, o bloco de instrução será uma seção crítica e `balance` nunca se tornará um número negativo.</span><span class="sxs-lookup"><span data-stu-id="b1f91-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 <span data-ttu-id="b1f91-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1f91-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b1f91-126">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b1f91-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1f91-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1f91-127">See Also</span></span>  
 <span data-ttu-id="b1f91-128"><xref:System.Reflection.MethodImplAttributes></span><span class="sxs-lookup"><span data-stu-id="b1f91-128"><xref:System.Reflection.MethodImplAttributes></span></span>   
 <span data-ttu-id="b1f91-129"><xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="b1f91-129"><xref:System.Threading.Mutex></span></span>   
 <span data-ttu-id="b1f91-130">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1f91-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b1f91-131">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1f91-131">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b1f91-132">[Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span><span class="sxs-lookup"><span data-stu-id="b1f91-132">[Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span></span>  
 <span data-ttu-id="b1f91-133">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1f91-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b1f91-134">[Palavras-chave de instrução](../../../csharp/language-reference/keywords/statement-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="b1f91-134">[Statement Keywords](../../../csharp/language-reference/keywords/statement-keywords.md) </span></span>  
 <span data-ttu-id="b1f91-135">@System.Threading.Monitor</span><span class="sxs-lookup"><span data-stu-id="b1f91-135">@System.Threading.Monitor</span></span>   
 <span data-ttu-id="b1f91-136">[Operações interconectadas](../../../standard/threading/interlocked-operations.md) </span><span class="sxs-lookup"><span data-stu-id="b1f91-136">[Interlocked Operations](../../../standard/threading/interlocked-operations.md) </span></span>  
 <span data-ttu-id="b1f91-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span><span class="sxs-lookup"><span data-stu-id="b1f91-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span></span>  
 [<span data-ttu-id="b1f91-138">Sincronização de Thread </span><span class="sxs-lookup"><span data-stu-id="b1f91-138">Thread Synchronization</span></span>](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)

