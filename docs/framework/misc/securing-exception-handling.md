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
ms.openlocfilehash: bc8cd20a4183ffd002f1399b6b50c8956208a21b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868791"
---
# <a name="securing-exception-handling"></a>Protegendo a manipulação de exceções
No Visual C++ e Visual Basic, uma expressão de filtro ainda mais para cima na pilha é executado antes de qualquer **finalmente** instrução. O **catch** bloco associado a esse filtro é executado após o **finalmente** instrução. Para obter mais informações, consulte [Using User-Filtered exceções](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Esta seção examina as implicações de segurança desse pedido. Considere o seguinte exemplo de pseudocódigo que ilustra a ordem na quais instruções de filtro e **finalmente** declarações são executadas.  
  
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
  
 O filtro é executado antes do **finalmente** instrução, portanto, problemas de segurança podem ser introduzidos por qualquer coisa que faz com que um estado em que a execução de outro código poderia se beneficiar as alterações. Por exemplo:  
  
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
  
 Este pseudocódigo permite que um filtro superior na pilha para executar código arbitrário. Outros exemplos de operações que tem um efeito semelhante são temporária representação da identidade de outro, definir um sinalizador interno que ignora a alguma verificação de segurança, ou mudar a cultura associada ao thread. A solução recomendada é apresentar um manipulador de exceção para isolar as alterações do código para o estado de thread em blocos de filtro de chamadores. No entanto, é importante que o manipulador de exceção ser introduzidas corretamente ou não esse problema será corrigido. O exemplo a seguir alterna para a cultura de interface do usuário, mas qualquer tipo de alteração de estado de thread pode ser exposto da mesma forma.  
  
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
  
 Nesse caso, a correção certa é encapsular existente **tente**/**finalmente** bloco em um **tente**/**catch** bloco. Simplesmente apresentando uma **catch-throw** cláusula à existente **tente**/**finalmente** bloco não corrigir o problema, conforme mostrado no exemplo a seguir.  
  
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
  
 Isso não corrigir o problema porque o **finalmente** instrução não foi executado antes de `FilterFunc` obtém controle.  
  
 O exemplo a seguir corrige o problema, garantindo que o **finalmente** cláusula foi executada antes de oferecer uma exceção blocos de filtro de exceção dos chamadores.  
  
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

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
