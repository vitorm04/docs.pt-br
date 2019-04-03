---
title: 'Como: Chamar um método de extensão (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 2543694e6bf8da5b67ecaccc92633a8448154063
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837112"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Como: Chamar um método de extensão (Visual Basic)
Métodos de extensão permitem adicionar métodos a uma classe existente. Depois que um método de extensão é declarado e colocado no escopo, você pode chamá-lo como um método de instância do tipo que ele estende. Para obter mais informações sobre como escrever um método de extensão, consulte [como: Escrever um método de extensão](./how-to-write-an-extension-method.md).  
  
 As instruções a seguir se referem ao método de extensão `PrintAndPunctuate`, que exibirá a instância de cadeia de caracteres que invoca, seguido por qualquer valor é enviado para o segundo parâmetro, `punc`.  
  
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
  
 O método deve estar no escopo quando ela é chamada.  
  
### <a name="to-call-an-extension-method"></a>Para chamar um método de extensão  
  
1.  Declare uma variável que tem o tipo de dados do primeiro parâmetro do método de extensão. Para `PrintAndPunctuate`, é necessário um <xref:System.String> variável:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Que a variável invocará o método de extensão, e seu valor está associado ao primeiro parâmetro, `aString`. A seguinte instrução de chamada exibirá `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Observe que a chamada para esse método de extensão procura apenas como uma chamada para qualquer um do <xref:System.String> métodos que exigem um parâmetro da instância:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Declarar outra variável de cadeia de caracteres e chame o método novamente para ver se ele funciona com qualquer cadeia de caracteres.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Dessa vez, o resultado é: `or not!!!`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir é um exemplo completo da criação e uso de um método de extensão simples.  
  
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

- [Como: Escrever um método de extensão](./how-to-write-an-extension-method.md)
- [Métodos de Extensão](./extension-methods.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
