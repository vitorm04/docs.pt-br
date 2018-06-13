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
ms.openlocfilehash: fe978930a9f84e0084f79f5fe585a1ecc3bf4eb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393036"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="6f225-102">Protegendo a manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="6f225-102">Securing Exception Handling</span></span>
<span data-ttu-id="6f225-103">No Visual C++ e Visual Basic, uma expressão de filtro mais acima na pilha é executado antes de qualquer **finalmente** instrução.</span><span class="sxs-lookup"><span data-stu-id="6f225-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="6f225-104">O **catch** bloco associado que o filtro é executado após o **finalmente** instrução.</span><span class="sxs-lookup"><span data-stu-id="6f225-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="6f225-105">Para obter mais informações, consulte [Using User-Filtered exceções](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="6f225-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="6f225-106">Esta seção examina as implicações de segurança desse pedido.</span><span class="sxs-lookup"><span data-stu-id="6f225-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="6f225-107">Considere o seguinte exemplo de pseudocódigo que ilustra a ordem na qual instruções de filtro e **finalmente** declarações são executadas.</span><span class="sxs-lookup"><span data-stu-id="6f225-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="6f225-108">Esse código imprime a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f225-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="6f225-109">O filtro é executado antes do **finalmente** instrução, para problemas de segurança podem ser introduzidos por tudo o que faz um estado em que a execução de outro código poderia se beneficiar.</span><span class="sxs-lookup"><span data-stu-id="6f225-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="6f225-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6f225-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="6f225-111">Este pseudocódigo permite que um filtro de nível superior da pilha para executar um código arbitrário.</span><span class="sxs-lookup"><span data-stu-id="6f225-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="6f225-112">Outros exemplos de operações que teriam um efeito semelhante são temporária representação da identidade de outra, definir um sinalizador interno que ignora alguma verificação de segurança, ou alterar a cultura associada ao thread.</span><span class="sxs-lookup"><span data-stu-id="6f225-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="6f225-113">A solução recomendada é apresentar um manipulador de exceção para isolar alterações do código para o estado de thread em blocos de filtro dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="6f225-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="6f225-114">No entanto, é importante que o manipulador de exceção ser introduzido corretamente ou não esse problema será corrigido.</span><span class="sxs-lookup"><span data-stu-id="6f225-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="6f225-115">O exemplo a seguir alterna a cultura de interface do usuário, mas qualquer tipo de alteração de estado de thread que poderia ser exposto da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="6f225-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="6f225-116">Nesse caso é a correção correta encapsular existente **tente**/**finalmente** bloco em um **tente**/**catch** bloco.</span><span class="sxs-lookup"><span data-stu-id="6f225-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="6f225-117">Simplesmente apresentando um **catch throw** cláusula em existente **tente**/**finalmente** bloco não corrigir o problema, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f225-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6f225-118">Isso não corrigir o problema, porque o **finalmente** instrução não foi executado antes do `FilterFunc` obtém controle.</span><span class="sxs-lookup"><span data-stu-id="6f225-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="6f225-119">O exemplo a seguir corrige o problema, garantindo que o **finalmente** cláusula executou antes de oferecer uma exceção blocos de filtro de exceção aos visitantes.</span><span class="sxs-lookup"><span data-stu-id="6f225-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f225-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f225-120">See Also</span></span>  
 [<span data-ttu-id="6f225-121">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="6f225-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
