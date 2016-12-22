---
title: "Como ocultar uma vari&#225;vel herdada (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instruções de declaração, elementos declarados"
  - "elementos declarados, sobre elementos declarados"
  - "elementos declarados, referenciando"
  - "nomes de elementos, qualificação"
  - "qualificação, de nomes de elementos"
  - "referências, elementos declarados"
  - "fazendo referência a elementos declarados"
  - "variáveis [Visual Basic], ocultação herdada"
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ocultar uma vari&#225;vel herdada (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma classe derivada herda todas as definições de sua classe base.  Se você deseja definir uma variável usando o mesmo nome que um elemento da classe base, você pode ocultar, ou *sombrear*, aquele elemento de classe base quando você define sua variável na classe derivada.  Se você fizer isso, código na classe derivada acessa sua variável a não ser que ele circunde explicitamente o mecanismo de sombreamento.  
  
 Outra razão pela qual você possa desejar ocultar uma variável é protegê\-la da revisão de classe base.  A classe base pode passar por uma mudança que altere o elemento o qual você está herdando.  Se isto acontecer, o modificador `Shadows` obriga referências da classe derivada a serem resolvidas a sua variável, em vez do elemento de classe base.  
  
### Para ocultar uma variável herdada  
  
1.  Certifique\-se de que a variável que você deseja usar esteja declarada a nível de classe \(fora de qualquer procedimento\).  Caso cntrário você não precisa ocultá\-lo.  
  
2.  Dentro de sua classe derivada, escreva um [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarando sua variável.  Use o mesmo nome que aquele da variável herdada.  
  
3.  Inclua a palavra\-chave [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) na declaração.  
  
     Quando código na classe derivada refere\-se ao nome da variável, o compilador resolve a referência a sua variável.  
  
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
  
     O exemplo precedente declara a variável `shadowString` na classe base e a sombreia na classe derivada.  O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está habilitado.  Isso então exibe a versão sombreada quando `shadowString` esa habilitado com a palavra\-chave `MyBase`.  
  
## Programação robusta  
 Sombreamento introduz mais de uma versão de uma variável com o mesmo nome.  Quando uma declaração de código refere\-se ao nome da variável, a versão a qual o compilador resolve a referência depende de fatores tais como a localização da declaração de código e a presença de cadeia de caracteres de habilitação.  Isto pode aumentar o risco de referir\-se a uma versão não planejada de uma variável sombreada.  Você pode reduzir aquele risco habilitando todas as referências a uma variável sombreada.  
  
## Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [Como ocultar uma variável com o mesmo nome que a variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [Como acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções básicas de herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)