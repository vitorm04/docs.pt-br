---
title: Como chamar um método de extensão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 32691183bcd1632a82b1e9a2668790abbf8f80fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Como chamar um método de extensão (Visual Basic)
Métodos de extensão permitem adicionar métodos a uma classe existente. Depois que um método de extensão é declarado e colocado no escopo, você pode chamá-lo como um método de instância do tipo que ele estende. Para obter mais informações sobre como escrever um método de extensão, consulte [como: gravar um método de extensão](./how-to-write-an-extension-method.md).  
  
 Consultem as instruções a seguir para o método de extensão `PrintAndPunctuate`, que exibirá a instância de cadeia de caracteres que o chama, seguido de qualquer valor que será enviada para o segundo parâmetro, `punc`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 O método deve ser no escopo quando ela é chamada.  
  
### <a name="to-call-an-extension-method"></a>Para chamar um método de extensão  
  
1.  Declare uma variável que tem o tipo de dados do primeiro parâmetro do método de extensão. Para `PrintAndPunctuate`, é necessário um <xref:System.String> variável:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Que a variável chamará o método de extensão, e seu valor é vinculado ao primeiro parâmetro, `aString`. Exibirá a seguinte instrução de chamada `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Observe que a chamada para esse método de extensão é apenas como uma chamada para qualquer uma da <xref:System.String> métodos que exigem um parâmetro da instância:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Declarar a outra variável de cadeia de caracteres e chame o método novamente para ver se ele funciona com qualquer cadeia de caracteres.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Dessa vez, o resultado é: `or not!!!`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir é um exemplo completo de criação e uso de um método de extensão simples.  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como escrever um método de extensão](./how-to-write-an-extension-method.md)  
 [Métodos de Extensão](./extension-methods.md)  
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
