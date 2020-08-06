---
title: Protegendo a manipulação de exceções
description: Veja como tornar o tratamento de exceções seguro no código .NET. Examine a ordem em que o código é executado se houver instruções Try, Except, catch e finally.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: c7643bb34da0cbcbd267fc90e6294bc0b565985e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855771"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="84096-104">Protegendo a manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="84096-104">Securing Exception Handling</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="84096-105">Em Visual C++ e Visual Basic, uma expressão de filtro mais acima da pilha é executada antes de qualquer `finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="84096-105">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any `finally` statement.</span></span> <span data-ttu-id="84096-106">O bloco **Catch** associado a esse filtro é executado após a `finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="84096-106">The **catch** block associated with that filter runs after the `finally` statement.</span></span> <span data-ttu-id="84096-107">Para obter mais informações, consulte [usando exceções filtradas pelo usuário](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="84096-107">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="84096-108">Esta seção examina as implicações de segurança deste pedido.</span><span class="sxs-lookup"><span data-stu-id="84096-108">This section examines the security implications of this order.</span></span> <span data-ttu-id="84096-109">Considere o seguinte exemplo de pseudocódigo que ilustra a ordem em que as instruções de filtro e as `finally` instruções são executadas.</span><span class="sxs-lookup"><span data-stu-id="84096-109">Consider the following pseudocode example that illustrates the order in which filter statements and `finally` statements run.</span></span>  
  
```cpp  
void Main()
{  
    try
    {  
        Sub();  
    }
    except (Filter())
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()
{  
    try
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }
    finally
    {  
        Console.WriteLine("finally");  
    }  
}
```  
  
 <span data-ttu-id="84096-110">Esse código imprime o seguinte.</span><span class="sxs-lookup"><span data-stu-id="84096-110">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="84096-111">O filtro é executado antes da `finally` instrução, portanto, problemas de segurança podem ser introduzidos por qualquer coisa que faça uma alteração de estado em que a execução de outro código possa tirar proveito.</span><span class="sxs-lookup"><span data-stu-id="84096-111">The filter runs before the `finally` statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="84096-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="84096-112">For example:</span></span>  
  
```cpp  
try
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and
    // so on) that could be exploited if malicious
    // code ran before state is restored.  
    Do_some_work();  
}
finally
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 <span data-ttu-id="84096-113">Esse pseudocódigo permite que um filtro acima da pilha execute um código arbitrário.</span><span class="sxs-lookup"><span data-stu-id="84096-113">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="84096-114">Outros exemplos de operações que teriam um efeito semelhante são a representação temporária de outra identidade, a definição de um sinalizador interno que ignora alguma verificação de segurança ou a alteração da cultura associada ao thread.</span><span class="sxs-lookup"><span data-stu-id="84096-114">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="84096-115">A solução recomendada é introduzir um manipulador de exceção para isolar as alterações do código no estado do thread dos blocos de filtro dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="84096-115">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="84096-116">No entanto, é importante introduzir corretamente o manipulador de exceção ou esse problema não será corrigido.</span><span class="sxs-lookup"><span data-stu-id="84096-116">However, it's important to properly introduce the exception handler or this problem won't be fixed.</span></span> <span data-ttu-id="84096-117">O exemplo a seguir alterna a cultura da interface do usuário, mas qualquer tipo de alteração de estado de thread pode ser exposta de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="84096-117">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 <span data-ttu-id="84096-118">A correção correta nesse caso é encapsular o bloco **try** / **finally** existente em um bloco **try** / **Catch** .</span><span class="sxs-lookup"><span data-stu-id="84096-118">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="84096-119">Simplesmente introduzir uma cláusula **Catch-throw** no bloco **try** / **finally** existente não corrige o problema, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="84096-119">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 <span data-ttu-id="84096-120">Isso não corrige o problema porque a `finally` instrução não foi executada antes do `FilterFunc` controle Gets.</span><span class="sxs-lookup"><span data-stu-id="84096-120">This does not fix the problem because the `finally` statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="84096-121">O exemplo a seguir corrige o problema, garantindo que a `finally` cláusula tenha sido executada antes de oferecer uma exceção dos blocos de filtro de exceção dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="84096-121">The following example fixes the problem by ensuring that the `finally` clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try
    {  
        try
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="84096-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="84096-122">See also</span></span>

- [<span data-ttu-id="84096-123">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="84096-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
