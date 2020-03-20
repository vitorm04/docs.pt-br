---
title: Protegendo a manipulação de exceções
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181144"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="063eb-102">Protegendo a manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="063eb-102">Securing Exception Handling</span></span>
<span data-ttu-id="063eb-103">No Visual C++ e Visual Basic, uma expressão de filtro mais acima da pilha é executada antes de qualquer **declaração finalmente.**</span><span class="sxs-lookup"><span data-stu-id="063eb-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="063eb-104">O bloco **de captura** associado a esse filtro é executado após a **declaração finalmente.**</span><span class="sxs-lookup"><span data-stu-id="063eb-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="063eb-105">Para obter mais informações, consulte [Usando exceções filtradas pelo usuário](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="063eb-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="063eb-106">Esta seção examina as implicações de segurança desta ordem.</span><span class="sxs-lookup"><span data-stu-id="063eb-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="063eb-107">Considere o seguinte exemplo de pseudocódigo que ilustra a ordem em que as instruções de filtro e **finalmente** as instruções são executadas.</span><span class="sxs-lookup"><span data-stu-id="063eb-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="063eb-108">Este código imprime o seguinte.</span><span class="sxs-lookup"><span data-stu-id="063eb-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="063eb-109">O filtro é executado antes da **declaração finalmente,** para que os problemas de segurança possam ser introduzidos por qualquer coisa que faça uma alteração de estado onde a execução de outro código possa tirar vantagem.</span><span class="sxs-lookup"><span data-stu-id="063eb-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="063eb-110">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="063eb-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="063eb-111">Este pseudocódigo permite que um filtro mais acima da pilha execute código arbitrário.</span><span class="sxs-lookup"><span data-stu-id="063eb-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="063eb-112">Outros exemplos de operações que teriam um efeito semelhante são a representação temporária de outra identidade, a configuração de uma bandeira interna que ignora alguma verificação de segurança ou altera a cultura associada ao segmento.</span><span class="sxs-lookup"><span data-stu-id="063eb-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="063eb-113">A solução recomendada é introduzir um manipulador de exceção para isolar as alterações do código no estado de thread dos blocos de filtro dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="063eb-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="063eb-114">No entanto, é importante que o manipulador de exceção seja devidamente introduzido ou este problema não será corrigido.</span><span class="sxs-lookup"><span data-stu-id="063eb-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="063eb-115">O exemplo a seguir muda a cultura de IU, mas qualquer tipo de alteração do estado de segmento pode ser igualmente exposta.</span><span class="sxs-lookup"><span data-stu-id="063eb-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="063eb-116">A correção correta neste caso é envolver a **tentativa**/existente**finalmente** bloquear em um bloco de**captura** **de tentativa.**/</span><span class="sxs-lookup"><span data-stu-id="063eb-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="063eb-117">A simples introdução de uma cláusula **de catch-throw** no bloco **de tentativa**/existente**finalmente** não corrige o problema, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="063eb-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="063eb-118">Isso não resolve o problema porque a **declaração finalmente** não foi executada antes do `FilterFunc` controle.</span><span class="sxs-lookup"><span data-stu-id="063eb-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="063eb-119">O exemplo a seguir corrige o problema, garantindo que a cláusula **finalmente** tenha sido executada antes de oferecer uma exceção aos blocos de filtro de exceção dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="063eb-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="063eb-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="063eb-120">See also</span></span>

- [<span data-ttu-id="063eb-121">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="063eb-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
