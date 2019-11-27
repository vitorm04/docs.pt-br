---
title: Como chamar um método de extensão
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340404"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Como chamar um método de extensão (Visual Basic)

Os métodos de extensão permitem adicionar métodos a uma classe existente. Depois que um método de extensão é declarado e colocado no escopo, você pode chamá-lo como um método de instância do tipo que ele estende. Para obter mais informações sobre como escrever um método de extensão, consulte [How to: Write a Extension Method](./how-to-write-an-extension-method.md).

 As instruções a seguir se referem ao método de extensão `PrintAndPunctuate`, que exibirá a instância de cadeia de caracteres que a invoca, seguida por qualquer valor enviado para o segundo parâmetro, `punc`.

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

O método deve estar no escopo quando for chamado.

### <a name="to-call-an-extension-method"></a>Para chamar um método de extensão

1. Declare uma variável que tenha o tipo de dados do primeiro parâmetro do método de extensão. Por `PrintAndPunctuate`, você precisa de uma variável <xref:System.String>:

    ```vb
    Dim example = "Ready"
    ```

2. Essa variável invocará o método de extensão e seu valor será associado ao primeiro parâmetro, `aString`. A instrução de chamada a seguir exibirá `Ready?`.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Observe que a chamada para esse método de extensão é semelhante a uma chamada para qualquer um dos métodos de instância de <xref:System.String> que exigem um parâmetro:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Declare outra variável de cadeia de caracteres e chame o método novamente para ver que ele funciona com qualquer cadeia de caracteres.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     O resultado desta vez é: `or not!!!`.

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

- [Como escrever um método de extensão](./how-to-write-an-extension-method.md)
- [Métodos de Extensão](./extension-methods.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
