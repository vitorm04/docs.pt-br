---
title: "Protegendo a manipulação de exceções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a>Protegendo a manipulação de exceções
No Visual C++ e Visual Basic, uma expressão de filtro mais acima na pilha é executado antes de qualquer **finalmente** instrução. O **catch** bloco associado que o filtro é executado após o **finalmente** instrução. Para obter mais informações, consulte [Using User-Filtered exceções](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Esta seção examina as implicações de segurança desse pedido. Considere o seguinte exemplo de pseudocódigo que ilustra a ordem na qual instruções de filtro e **finalmente** declarações são executadas.  
  
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
  
 Esse código imprime a seguir.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 O filtro é executado antes do **finalmente** instrução, para problemas de segurança podem ser introduzidos por tudo o que faz um estado em que a execução de outro código poderia se beneficiar. Por exemplo:  
  
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
  
 Este pseudocódigo permite que um filtro de nível superior da pilha para executar um código arbitrário. Outros exemplos de operações que teriam um efeito semelhante são temporária representação da identidade de outra, definir um sinalizador interno que ignora alguma verificação de segurança, ou alterar a cultura associada ao thread. A solução recomendada é apresentar um manipulador de exceção para isolar alterações do código para o estado de thread em blocos de filtro dos chamadores. No entanto, é importante que o manipulador de exceção ser introduzido corretamente ou não esse problema será corrigido. O exemplo a seguir alterna a cultura de interface do usuário, mas qualquer tipo de alteração de estado de thread que poderia ser exposto da mesma forma.  
  
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
  
 Nesse caso é a correção correta encapsular existente **tente**/**finalmente** bloco em um **tente**/**catch** bloco. Simplesmente apresentando um **catch throw** cláusula em existente **tente**/**finalmente** bloco não corrigir o problema, conforme mostrado no exemplo a seguir.  
  
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
  
 Isso não corrigir o problema, porque o **finalmente** instrução não foi executado antes do `FilterFunc` obtém controle.  
  
 O exemplo a seguir corrige o problema, garantindo que o **finalmente** cláusula executou antes de oferecer uma exceção blocos de filtro de exceção aos visitantes.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
