---
title: "Como: acessar uma variável ocultada por uma classe derivada (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- qualification, of element names
- base classes, accessing elements
- element names, qualification
- references, declared elements
- declared elements, referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 93d32120b23697f9886b4b9ad55a8f1957577930
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Como acessar uma variável oculta por uma classe derivada (Visual Basic)
Quando o código em uma classe derivada acessa uma variável, o compilador resolve normalmente a referência para a versão mais acessível, ou seja, a versão acessível as menor etapas derivacionais para trás da classe de acesso. Se a variável é definida na classe derivada, o código normalmente acessa essa definição.  
  
 Se a variável de classe derivada sombreia uma variável na classe base, ele oculta a versão da classe base. No entanto, você pode acessar a variável de classe base usando o `MyBase` palavra-chave.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Para acessar uma variável ocultada por uma classe derivada da classe base  
  
-   Em uma expressão ou instrução de atribuição, preceda o nome da variável com o `MyBase` palavra-chave e um período (`.`).  
  
     O compilador resolve a referência à versão da classe base da variável.  
  
     O exemplo a seguir ilustra sombreamento através de herança. Ele faz duas referências, que acessa a variável de sombreamento e outra que ignora o sombreamento.  
  
    ```  
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
  
     O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada. O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está qualificado. Em seguida, exibe a versão sombreada quando `shadowString` qualificado com o `MyBase` palavra-chave.  
  
## <a name="robust-programming"></a>Programação robusta  
 Para reduzir o risco de se referir a uma versão não intencional de uma variável sombreada, você pode qualificar totalmente todas as referências a uma variável sombreada. Sombreamento introduz mais de uma versão de uma variável com o mesmo nome. Quando uma declaração de código refere-se ao nome da variável, a versão para que o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação. Isso pode aumentar o risco de se referir à versão errada da variável.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [Como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [Como: ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
