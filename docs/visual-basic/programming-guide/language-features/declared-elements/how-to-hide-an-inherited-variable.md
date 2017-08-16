---
title: "Como: ocultar uma variável herdada (Visual Basic) | Documentos do Microsoft"
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
- element names, qualification
- references, declared elements
- declaration statements, declared elements
- referencing declared elements
- declared elements, referencing
- declared elements, about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 4cd3b9b643bbf511b4b85d6d4cddcdab61b8d11b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Como ocultar uma variável herdada (Visual Basic)
Uma classe derivada herda todas as definições de sua classe base. Se você quiser definir uma variável usando o mesmo nome como um elemento da classe base, você pode ocultar, ou *sombra*, esse elemento de classe base quando você define sua variável na classe derivada. Se você fizer isso, o código na classe derivada acessa sua variável, a menos que explicitamente ignora o mecanismo de sombreamento.  
  
 Outro motivo, que talvez você queira ocultar uma variável herdada é proteger contra a revisão de classe base. A classe base pode passar por uma mudança que altere o elemento que você está herdando. Se isso acontecer, o `Shadows` modificador obriga referências da classe derivada a ser resolvido para a variável, em vez de para o elemento de classe base.  
  
### <a name="to-hide-an-inherited-variable"></a>Para ocultar uma variável herdada  
  
1.  Certifique-se de que a variável que você deseja ocultar é declarada no nível de classe (fora de qualquer procedimento). Caso contrário, você não precisa ocultá-lo.  
  
2.  Dentro de sua classe derivada, escreva um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarando sua variável. Use o mesmo nome da variável herdada.  
  
3.  Incluir o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave na declaração.  
  
     Quando o código na classe derivada refere-se ao nome da variável, o compilador resolve a referência à variável.  
  
     O exemplo a seguir ilustra sombreamento de uma variável herdada.  
  
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
 Sombreamento introduz mais de uma versão de uma variável com o mesmo nome. Quando uma declaração de código refere-se ao nome da variável, a versão para que o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação. Isso pode aumentar o risco de se referir a uma versão não intencional de uma variável sombreada. Você pode diminuir esse risco qualificar totalmente todas as referências a uma variável sombreada.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [Como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [Como: acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
