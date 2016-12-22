---
title: "Como acessar uma vari&#225;vel oculta por uma classe derivada (Visual Basic) | Microsoft Docs"
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
  - "classes base, acessando elementos"
  - "elementos declarados, referenciando"
  - "nomes de elementos, qualificação"
  - "qualificação, de nomes de elementos"
  - "referências, elementos declarados"
  - "variáveis [Visual Basic], acessando ocultos"
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como acessar uma vari&#225;vel oculta por uma classe derivada (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando o código em uma classe derivada acessa uma variável, o compilador resolve normalmente a referência para a versão acessível mais próxima, ou seja, a versão acessível as etapas de derivational mais baixas para trás da classe ao acessar.  Se a variável é definida na classe derivada, o código acessa normalmente essa definição.  
  
 Se a variável de classe derivada é sombra de uma variável na classe base, ele oculta a versão da classe base.  No entanto, você pode acessar a variável de classe base, qualificá\-la com o `MyBase` palavra\-chave.  
  
### Para acessar uma variável ocultada por uma classe derivada da classe base  
  
-   Em uma expressão ou instrução de atribuição, preceda o nome da variável com o `MyBase` palavra\-chave e um período \(`.`\).  
  
     O compilador resolve a referência para a versão de classe base da variável.  
  
     O exemplo a seguir ilustra o sombreamento através de herança.  Ele faz duas referências, aquele que acessa a variável de sombreamento e uma que ignora o efeito de sombra.  
  
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
  
     O exemplo precedente declara a variável `shadowString` na classe base e a sombreia na classe derivada.  O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está habilitado.  Isso então exibe a versão sombreada quando `shadowString` esa habilitado com a palavra\-chave `MyBase` .  
  
## Programação robusta  
 Para reduzir o risco de se referir a uma versão não pretendida de uma variável sombreada, você pode qualificar totalmente todas as referências a uma variável sombreada.  Sombreamento introduz mais de uma versão de uma variável com o mesmo nome.  Quando uma declaração de código refere\-se ao nome da variável, a versão a qual o compilador resolve a referência depende de fatores tais como a localização da declaração de código e a presença de cadeia de caracteres de habilitação.  Isso pode aumentar o risco de se referir à versão errada da variável.  
  
## Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [Como ocultar uma variável com o mesmo nome que a variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [Como ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções básicas de herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)