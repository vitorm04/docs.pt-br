---
title: "Como ocultar uma variável herdada (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2059da873f8b9ec9ea51191139c652a9e01d92b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Como ocultar uma variável herdada (Visual Basic)
Uma classe derivada herda todas as definições de sua classe base. Se você quiser definir uma variável usando o mesmo nome que um elemento da classe base, você pode ocultar, ou *sombra*, esse elemento de classe base quando você define sua variável na classe derivada. Se você fizer isso, o código na classe derivada acessa sua variável, a menos que explicitamente ignora o mecanismo de sombreamento.  
  
 Outro motivo, que talvez você queira ocultar uma variável herdada é proteger contra a revisão de classe base. A classe base pode passar por uma mudança que altere o elemento que são herdadas. Se isso acontecer, o `Shadows` modificador obriga referências da classe derivada a ser resolvido para a variável, em vez de para o elemento de classe base.  
  
### <a name="to-hide-an-inherited-variable"></a>Para ocultar uma variável herdada  
  
1.  Certifique-se de que a variável que você deseja ocultar é declarada no nível de classe (fora de qualquer procedimento). Caso contrário, você não precisa ocultá-lo.  
  
2.  Dentro de sua classe derivada, escreva uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarar a variável. Use o mesmo nome da variável herdada.  
  
3.  Incluir o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave na declaração.  
  
     Quando o código na classe derivada refere-se ao nome da variável, o compilador resolve a referência à sua variável.  
  
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
  
     O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada. O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está qualificado. Em seguida, exibe a versão sombreada quando `shadowString` é qualificado com o `MyBase` palavra-chave.  
  
## <a name="robust-programming"></a>Programação robusta  
 Sombreamento apresenta mais de uma versão de uma variável com o mesmo nome. Quando uma declaração de código se refere ao nome da variável, a versão para o qual o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação. Isso pode aumentar o risco de fazer referência a uma versão não intencional de uma variável sombreada. Você pode reduzir esse risco qualificando totalmente todas as referências a uma variável sombreada.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Como ocultar uma variável com o mesmo nome que a variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Como acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
