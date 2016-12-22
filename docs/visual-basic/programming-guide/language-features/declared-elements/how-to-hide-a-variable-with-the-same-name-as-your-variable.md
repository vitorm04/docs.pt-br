---
title: "Como ocultar uma vari&#225;vel com o mesmo nome que a vari&#225;vel (Visual Basic) | Microsoft Docs"
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
  - "declarações, elementos"
  - "elementos declarados, sobre elementos declarados"
  - "elementos declarados, referenciando"
  - "declarando elementos"
  - "nomes de elementos, qualificação"
  - "qualificação, de nomes de elementos"
  - "referências, elementos declarados"
  - "fazendo referência a elementos declarados"
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ocultar uma vari&#225;vel com o mesmo nome que a vari&#225;vel (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode ocultar uma variável por  *sombreamento* \-lo, ou seja, redefinindo\-lo com uma variável de mesmo nome.  Você pode sombrear a variável que você deseja ocultar de duas maneiras:  
  
-   **Sombrear por meio de escopo.** Você pode sombreá\-lo por meio do escopo por redeclaring\-lo dentro de uma sub\-região da região que contém a variável que você deseja ocultar.  
  
-   **Sombrear através de herança.** Se a variável que você deseja ocultar é definida no nível de classe, você pode sombreá\-lo por meio de herança por redeclaring\-lo com o [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra\-chave em uma classe derivada.  
  
## Duas maneiras para ocultar uma variável.  
  
#### Para ocultar uma variável pelo efeito de sombra por meio de escopo  
  
1.  Determinar a região definindo a variável que você deseja ocultar e determinar uma sub\-região na qual deseja redefini\-la com sua variável.  
  
    |Região da variável|Sub\-região permitido para redefinindo\-lo|  
    |------------------------|------------------------------------------------|  
    |Module|Uma classe dentro do módulo|  
    |Classe|Uma subclasse da classe<br /><br /> Um procedimento dentro da classe|  
  
     Não é possível redefinir uma variável de procedimento em um bloco dentro desse procedimento, por exemplo em um `If`...`End If` construção ou um `For` loop.  
  
2.  Se ele ainda não existir, crie a sub\-região.  
  
3.  Dentro da sub\-região, escrever um [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarando a variável de sombreamento.  
  
     Quando o código dentro a sub\-região refere\-se ao nome da variável, o compilador resolve a referência à variável de sombreamento.  
  
     O exemplo a seguir ilustra o sombreamento através de escopo, bem como uma referência que ignora o efeito de sombra.  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     O exemplo anterior declara a variável `num` no nível de módulo e no nível de procedimento \(no procedimento `show`\).  A variável local `num` sombreia a variável de nível de módulo `num` em `show`, portanto, a variável local é definida como 2.  No entanto, não há nenhuma variável de local a sombra `num` na `useModuleLevelNum` procedimento.  Portanto, `useModuleLevelNum` define o valor da variável nível de módulo como 1.  
  
     O `MsgBox` chamar dentro de `show` passará pelo mecanismo de sombreamento qualificando `num` com o nome do módulo.  Portanto, ele exibe a variável de nível de módulo em vez da variável local.  
  
#### Para ocultar uma variável pelo efeito de sombra por meio de herança  
  
1.  Certifique\-se de que a variável que você deseja ocultar é declarada em uma classe e no nível de classe \(fora de qualquer procedimento\).  Caso contrário, ele não pode sombrear através de herança.  
  
2.  Defina uma classe derivada da classe da variável, se ainda não existir.  
  
3.  Dentro da classe derivada, escrever um `Dim` declarando sua variável de instrução.  Inclua a palavra\-chave [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) na declaração.  
  
     Quando código na classe derivada refere\-se ao nome da variável, o compilador resolve a referência a sua variável.  
  
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
  
     O exemplo precedente declara a variável `shadowString` na classe base e a sombreia na classe derivada.  O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está habilitado.  Ele exibe a versão sombreada quando `shadowString` é qualificado com o `MyBase`palavra\-chave.  
  
## Programação robusta  
 Sombreamento introduz mais de uma versão de uma variável com o mesmo nome.  Quando uma declaração de código refere\-se ao nome da variável, a versão a qual o compilador resolve a referência depende de fatores tais como a localização da declaração de código e a presença de cadeia de caracteres de habilitação.  Isto pode aumentar o risco de referir\-se a uma versão não planejada de uma variável sombreada.  Você pode reduzir aquele risco habilitando todas as referências a uma variável sombreada.  
  
## Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [Como ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Como acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções básicas de herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)