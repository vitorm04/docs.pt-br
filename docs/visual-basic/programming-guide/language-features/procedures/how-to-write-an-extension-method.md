---
title: 'Como: Gravar um método de extensão (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631024"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Como: Gravar um método de extensão (Visual Basic)
Os métodos de extensão permitem adicionar métodos a uma classe existente. O método de extensão pode ser chamado como se fosse uma instância dessa classe.

### <a name="to-define-an-extension-method"></a>Para definir um método de extensão

1. Abra um aplicativo Visual Basic novo ou existente no Visual Studio.

2. Na parte superior do arquivo no qual você deseja definir um método de extensão, inclua a seguinte instrução de importação:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. Dentro de um módulo em seu aplicativo novo ou existente, inicie a definição do método com o atributo de extensão:

    ```vb
    <Extension()>
    ```

4. Declare seu método de forma comum, exceto que o tipo do primeiro parâmetro deve ser o tipo de dados que você deseja estender.

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Exemplo
 O exemplo a seguir declara um método de extensão no `StringExtensions`módulo. Um segundo módulo, `Module1`, importa `StringExtensions` e chama o método. O método de extensão deve estar no escopo quando ele é chamado. O método `PrintAndPunctuate` de extensão <xref:System.String> estende a classe com um método que exibe a instância de cadeia de caracteres seguida por uma cadeia de caracteres de símbolos de pontuação enviada no como um parâmetro.
  
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
  
 Observe que o método é definido com dois parâmetros e é chamado com apenas um. O primeiro parâmetro, `aString`, na definição do método, é `example`vinculado a, a instância `String` do que chama o método. A saída do exemplo é a seguinte:
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Métodos de Extensão](./extension-methods.md)
- [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
