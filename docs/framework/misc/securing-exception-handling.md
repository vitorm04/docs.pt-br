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
# <a name="securing-exception-handling"></a>Protegendo a manipulação de exceções
No Visual C++ e Visual Basic, uma expressão de filtro mais acima da pilha é executada antes de qualquer **declaração finalmente.** O bloco **de captura** associado a esse filtro é executado após a **declaração finalmente.** Para obter mais informações, consulte [Usando exceções filtradas pelo usuário](../../standard/exceptions/using-user-filtered-exception-handlers.md). Esta seção examina as implicações de segurança desta ordem. Considere o seguinte exemplo de pseudocódigo que ilustra a ordem em que as instruções de filtro e **finalmente** as instruções são executadas.  
  
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
  
 Este código imprime o seguinte.  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 O filtro é executado antes da **declaração finalmente,** para que os problemas de segurança possam ser introduzidos por qualquer coisa que faça uma alteração de estado onde a execução de outro código possa tirar vantagem. Por exemplo:   
  
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
  
 Este pseudocódigo permite que um filtro mais acima da pilha execute código arbitrário. Outros exemplos de operações que teriam um efeito semelhante são a representação temporária de outra identidade, a configuração de uma bandeira interna que ignora alguma verificação de segurança ou altera a cultura associada ao segmento. A solução recomendada é introduzir um manipulador de exceção para isolar as alterações do código no estado de thread dos blocos de filtro dos chamadores. No entanto, é importante que o manipulador de exceção seja devidamente introduzido ou este problema não será corrigido. O exemplo a seguir muda a cultura de IU, mas qualquer tipo de alteração do estado de segmento pode ser igualmente exposta.  
  
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
  
 A correção correta neste caso é envolver a **tentativa**/existente**finalmente** bloquear em um bloco de**captura** **de tentativa.**/ A simples introdução de uma cláusula **de catch-throw** no bloco **de tentativa**/existente**finalmente** não corrige o problema, como mostrado no exemplo a seguir.  
  
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
  
 Isso não resolve o problema porque a **declaração finalmente** não foi executada antes do `FilterFunc` controle.  
  
 O exemplo a seguir corrige o problema, garantindo que a cláusula **finalmente** tenha sido executada antes de oferecer uma exceção aos blocos de filtro de exceção dos chamadores.  
  
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
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
