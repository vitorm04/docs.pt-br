---
title: Como acessar uma variável oculta por uma classe derivada
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 276cb1411c66e1f7205507a1b1053cc8642c7cb0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345400"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Como acessar uma variável oculta por uma classe derivada (Visual Basic)

Quando o código em uma classe derivada acessa uma variável, o compilador normalmente resolve a referência à versão acessível mais próxima, ou seja, a versão acessível o menor número de etapas de derivação para trás da classe de acesso. Se a variável for definida na classe derivada, o código normalmente acessará essa definição.

Se a variável de classe derivada sombreia uma variável na classe base, ela ocultará a versão da classe base. No entanto, você pode acessar a variável de classe base qualificando-a com a palavra-chave `MyBase`.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Para acessar uma variável de classe base ocultada por uma classe derivada

- Em uma expressão ou instrução de atribuição, preceda o nome da variável com a palavra-chave `MyBase` e um ponto (`.`).

    O compilador resolve a referência à versão da classe base da variável.

    O exemplo a seguir ilustra o sombreamento por meio de herança. Ele faz duas referências, uma que acessa a variável de sombreamento e outra que ignora o sombreamento.

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada. O procedimento `showStrings` na classe derivada exibe a versão de sombreamento da cadeia de caracteres quando o nome `shadowString` não é qualificado. Em seguida, ele exibe a versão sombreada quando `shadowString` é qualificado com a palavra-chave `MyBase`.

## <a name="robust-programming"></a>Programação robusta

Para reduzir o risco de se referir a uma versão não intencional de uma variável sombreada, você pode qualificar totalmente todas as referências a uma variável sombreada. O sombreamento apresenta mais de uma versão de uma variável com o mesmo nome. Quando uma instrução de código se refere ao nome da variável, a versão para a qual o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação. Isso pode aumentar o risco de se referir à versão errada da variável.

## <a name="see-also"></a>Consulte também

- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Sombreamento em Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Como ocultar uma variável com o mesmo nome que a variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Como ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
