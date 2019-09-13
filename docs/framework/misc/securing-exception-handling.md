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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 256d9c9b825081e3bcfafd6e0e09de825d046d20
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894548"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="7e73e-102">Protegendo a manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="7e73e-102">Securing Exception Handling</span></span>
<span data-ttu-id="7e73e-103">No Visual C++ e Visual Basic, uma expressão de filtro mais acima da pilha é executada antes de qualquer instrução **finally** .</span><span class="sxs-lookup"><span data-stu-id="7e73e-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="7e73e-104">O bloco **Catch** associado a esse filtro é executado após a instrução **finally** .</span><span class="sxs-lookup"><span data-stu-id="7e73e-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="7e73e-105">Para obter mais informações, consulte [usando exceções filtradas pelo usuário](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="7e73e-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="7e73e-106">Esta seção examina as implicações de segurança deste pedido.</span><span class="sxs-lookup"><span data-stu-id="7e73e-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="7e73e-107">Considere o seguinte exemplo de pseudocódigo que ilustra a ordem em que as instruções de filtro e as instruções **finally** são executadas.</span><span class="sxs-lookup"><span data-stu-id="7e73e-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="7e73e-108">Esse código imprime o seguinte.</span><span class="sxs-lookup"><span data-stu-id="7e73e-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="7e73e-109">O filtro é executado antes da instrução **finally** , portanto, problemas de segurança podem ser introduzidos por qualquer coisa que faça uma alteração de estado em que a execução de outro código pode tirar proveito.</span><span class="sxs-lookup"><span data-stu-id="7e73e-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="7e73e-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7e73e-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="7e73e-111">Esse pseudocódigo permite que um filtro acima da pilha execute um código arbitrário.</span><span class="sxs-lookup"><span data-stu-id="7e73e-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="7e73e-112">Outros exemplos de operações que teriam um efeito semelhante são a representação temporária de outra identidade, a definição de um sinalizador interno que ignora alguma verificação de segurança ou a alteração da cultura associada ao thread.</span><span class="sxs-lookup"><span data-stu-id="7e73e-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="7e73e-113">A solução recomendada é introduzir um manipulador de exceção para isolar as alterações do código no estado do thread dos blocos de filtro dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="7e73e-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="7e73e-114">No entanto, é importante que o manipulador de exceção seja introduzido corretamente ou esse problema não seja corrigido.</span><span class="sxs-lookup"><span data-stu-id="7e73e-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="7e73e-115">O exemplo a seguir alterna a cultura da interface do usuário, mas qualquer tipo de alteração de estado de thread pode ser exposta de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="7e73e-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="7e73e-116">A correção correta nesse caso é encapsular o bloco **try**/**finally** existente em um bloco **try**/**Catch** .</span><span class="sxs-lookup"><span data-stu-id="7e73e-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="7e73e-117">Simplesmente introduzir uma cláusula **Catch-throw** no bloco **try**/**finally** existente não corrige o problema, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7e73e-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="7e73e-118">Isso não corrige o problema porque a instrução **finally** não foi executada antes do `FilterFunc` controle Gets.</span><span class="sxs-lookup"><span data-stu-id="7e73e-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="7e73e-119">O exemplo a seguir corrige o problema garantindo que a cláusula **finally** tenha sido executada antes de oferecer uma exceção dos blocos de filtro de exceção dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="7e73e-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e73e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e73e-120">See also</span></span>

- [<span data-ttu-id="7e73e-121">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="7e73e-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
