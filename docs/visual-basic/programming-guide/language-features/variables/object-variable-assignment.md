---
title: Atribuição de variável do objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 59dea45511ba8d7d10c95cf17e47981124c532e4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631059"
---
# <a name="object-variable-assignment-visual-basic"></a>Atribuição de variável do objeto (Visual Basic)

Você usa uma instrução de atribuição normal para atribuir um objeto a uma variável de objeto. Você pode atribuir uma expressão de objeto ou a palavra-chave [Nothing](../../../../visual-basic/language-reference/nothing.md) , como ilustra o exemplo a seguir.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing`significa que não há nenhum objeto atribuído atualmente à variável.

## <a name="initialization"></a>Inicialização

Quando o código começar a ser executado, suas variáveis de objeto `Nothing`serão inicializadas para. Aquelas cujas declarações incluem inicialização são reinicializadas para os valores que você especifica quando as instruções de declaração são executadas.

Você pode incluir a inicialização em sua declaração usando a [nova](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave. As instruções de declaração a seguir declaram variáveis `testUri` de objeto e `ver` atribuem objetos específicos a elas. Cada um deles usa um dos construtores sobrecarregados da classe apropriada para inicializar o objeto.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Dissociação

Definir uma variável de objeto `Nothing` para interromper a associação da variável com qualquer objeto específico. Isso impede que você altere acidentalmente o objeto alterando a variável. Ele também permite que você teste se a variável de objeto aponta para um objeto válido, como mostra o exemplo a seguir.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Se o objeto ao qual sua variável se refere estiver em outro aplicativo, esse teste não poderá determinar se o aplicativo foi encerrado ou simplesmente invalidará o objeto.

Uma variável de objeto com um valor `Nothing` de também é chamada de *referência nula*.

## <a name="current-instance"></a>Instância atual

A *instância atual* de um objeto é aquela em que o código está sendo executado no momento. Como todo o código é executado dentro de um procedimento, a instância atual é aquela em que o procedimento foi invocado.

A `Me` palavra-chave age como uma variável de objeto que faz referência à instância atual. Se um procedimento não for [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), ele poderá usar a `Me` palavra-chave para obter um ponteiro para a instância atual. Procedimentos compartilhados não podem ser associados a uma instância específica de uma classe.

O `Me` uso do é particularmente útil para passar a instância atual para um procedimento em outro módulo. Por exemplo, suponha que você tenha um número de documentos XML e queira adicionar texto padrão a todos eles. O exemplo a seguir define um procedimento para fazer isso.

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

Cada objeto de documento XML poderia então chamar o procedimento e passar sua instância atual como um argumento. O exemplo a seguir demonstra isso.

```vb
addStandardText(Me)
```

## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Como: Declare uma variável de objeto e atribua um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Como: Fazer uma variável de objeto não se referir a nenhuma instância](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
