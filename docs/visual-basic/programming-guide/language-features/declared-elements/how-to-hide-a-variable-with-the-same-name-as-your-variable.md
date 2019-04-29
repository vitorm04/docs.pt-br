---
title: 'Como: Ocultar uma variável com o mesmo nome que sua variável (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: 744c7aed50690d5591d1e8248e121cb66ef39108
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794700"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Como: Ocultar uma variável com o mesmo nome que sua variável (Visual Basic)
Você pode ocultar uma variável por *sombreamento* -lo, ou seja, redefinindo-o com uma variável de mesmo nome. Você pode sombrear a variável que você deseja ocultar de duas maneiras:  
  
- **Sombreamento através de escopo.** Você pode sombreá-lo por meio do escopo redeclarando ele dentro uma sub-região da região que contém a variável que você deseja ocultar.  
  
- **Sombreamento através de herança.** Se a variável que você deseja ocultar é definida no nível de classe, você pode sombreá-lo por meio da herança redeclarando-lo com o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave em uma classe derivada.  
  
## <a name="two-ways-to-hide-a-variable"></a>Duas maneiras para ocultar uma variável  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Para ocultar uma variável de sombreamento-lo através de escopo  
  
1. Determinar a região definindo a variável que você deseja ocultar e determinar uma sub-região no qual redefini-lo com sua variável.  
  
    |Região da variável|Sub-região permitida para redefinir a ele|  
    |-----------------------|-------------------------------------------|  
    |Módulo|Uma classe dentro do módulo|  
    |Classe|Uma subclasse dentro da classe<br /><br /> Um procedimento dentro da classe|  
  
     Você não pode redefinir uma variável de procedimento em um bloco dentro desse procedimento, por exemplo em um `If`... `End If` construção ou um `For` loop.  
  
2. Se ele ainda não existir, crie a sub-região.  
  
3. Dentro da sub-região, escrever um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarando a variável de sombreamento.  
  
     Quando o código dentro de sub-região refere-se ao nome da variável, o compilador resolve a referência à variável de sombreamento.  
  
     O exemplo a seguir ilustra o sombreamento através de escopo, bem como uma referência que ignora o sombreamento.  
  
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
  
     O exemplo anterior declara a variável `num` no nível de módulo e no nível de procedimento (no procedimento `show`). A variável local `num` sombreia a variável de nível de módulo `num` dentro do `show`, portanto, a variável local é definida como 2. No entanto, não há nenhuma variável local a sombra `num` no `useModuleLevelNum` procedimento. Portanto, `useModuleLevelNum` define o valor da variável de nível de módulo como 1.  
  
     O `MsgBox` chamar dentro `show` ignora o mecanismo de sombreamento qualificando `num` com o nome do módulo. Portanto, ele exibe a variável de nível de módulo em vez da variável local.  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Para ocultar uma variável sombreando-lo por meio de herança  
  
1. Certifique-se de que a variável que você deseja ocultar é declarada em uma classe e no nível de classe (fora de qualquer procedimento). Caso contrário, você não pode sombreá-lo por meio da herança.  
  
2. Defina uma classe derivada da classe da variável, se ainda não existir.  
  
3. Dentro da classe derivada, escrever um `Dim` declarar sua variável de instrução. Incluir o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave na declaração.  
  
     Quando o código na classe derivada se refere ao nome da variável, o compilador resolve a referência à variável.  
  
     O exemplo a seguir ilustra o sombreamento através de herança. Ele faz duas referências, uma que acessa a variável de sombreamento e outra que ignora o sombreamento.  
  
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
  
     O exemplo anterior declara a variável `shadowString` na classe base e sombreia na classe derivada. O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não são qualificados. Ele então exibe a versão sombreada quando `shadowString` qualificado com o `MyBase` palavra-chave.  
  
## <a name="robust-programming"></a>Programação robusta  
 Sombreamento apresenta mais de uma versão de uma variável com o mesmo nome. Quando uma declaração de código refere-se ao nome da variável, a versão à qual o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação. Isso pode aumentar o risco de se referir a uma versão não intencional de uma variável sombreada. Você pode reduzir esse risco qualificar totalmente todas as referências a uma variável sombreada.  
  
## <a name="see-also"></a>Consulte também

- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Como: Ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Como: Acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
