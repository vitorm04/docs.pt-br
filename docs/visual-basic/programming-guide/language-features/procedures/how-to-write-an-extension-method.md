---
title: Como escrever um método de extensão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: e220a025c39757b492be033caeb8924523515804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Como escrever um método de extensão (Visual Basic)
Métodos de extensão permitem adicionar métodos a uma classe existente. O método de extensão pode ser chamado como se fosse uma instância dessa classe.  
  
### <a name="to-define-an-extension-method"></a>Para definir um método de extensão  
  
1.  Abra um aplicativo novo ou existente do Visual Basic no Visual Studio.  
  
2.  Na parte superior do arquivo no qual você deseja definir um método de extensão, inclua a seguinte instrução de importação:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  Dentro de um módulo em seu aplicativo novo ou existente, começa a definição de método com o atributo de extensão:  
  
    ```  
    <Extension()>  
    ```  
  
4.  Declare o método da maneira normal, exceto que o tipo do primeiro parâmetro deve ser do tipo de dados que você deseja estender.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara um método de extensão no módulo `StringExtensions`. Um segundo módulo, `Module1`, importa `StringExtensions` e chama o método. O método de extensão deve ser no escopo quando ele é chamado. Método de extensão `PrintAndPunctuate` estende o <xref:System.String> classe com um método que exibe a instância de cadeia de caracteres seguido por uma cadeia de caracteres de símbolos de pontuação enviado como um parâmetro.  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
```  
  
 Observe que o método é definido com dois parâmetros e chamado com apenas um. O primeiro parâmetro, `aString`, no método de definição está associada a `example`, a instância do `String` que chama o método. A saída do exemplo é o seguinte:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [Métodos de Extensão](./extension-methods.md)  
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
