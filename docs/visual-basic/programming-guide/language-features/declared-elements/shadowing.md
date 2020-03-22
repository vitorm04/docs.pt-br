---
title: Sombreamento
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266879"
---
# <a name="shadowing-in-visual-basic"></a>Sombreamento no Visual Basic
Quando dois elementos de programação compartilham o mesmo nome, um deles pode esconder, ou *sombra,* o outro. Em tal situação, o elemento sombreado não está disponível para referência; em vez disso, quando seu código usa o nome do elemento, o compilador Visual Basic resolve-o para o elemento de sombra.  
  
## <a name="purpose"></a>Finalidade  
 O principal objetivo da sombra é proteger a definição de seus membros da classe. A classe base pode sofrer uma mudança que cria um elemento com o mesmo nome que você já definiu. Se isso acontecer, o `Shadows` modificador força as referências através de sua classe a serem resolvidas ao membro que você definiu, em vez de ao novo elemento de classe base.  
  
## <a name="types-of-shadowing"></a>Tipos de Sombreamento  
 Um elemento pode sombrear outro elemento de duas maneiras diferentes. O elemento de sombreamento pode ser declarado dentro de uma sub-região da região contendo o elemento sombreado, nesse caso o sombreamento é realizado *através do escopo*. Ou uma classe derivada pode redefinir um membro de uma classe base, nesse caso o sombreamento é feito *através de herança.*  
  
### <a name="shadowing-through-scope"></a>Sombreamento através do escopo  
 É possível que elementos de programação no mesmo módulo, classe ou estrutura tenham o mesmo nome, mas escopo diferente. Quando dois elementos são declarados desta maneira e o código refere-se ao nome que compartilham, o elemento com o escopo mais estreito sombreia o outro elemento (o escopo do bloco é o mais estreito).  
  
 Por exemplo, um módulo `Public` pode `temp`definir uma variável nomeada , e um `temp`procedimento dentro do módulo pode declarar uma variável local também chamada . As referências de `temp` dentro do procedimento acessam a variável local, enquanto as referências de `temp` fora do procedimento acessam a `Public` variável. Neste caso, a `temp` variável procedimento sombreia a variável `temp`módulo .  
  
 A ilustração a seguir mostra `temp`duas variáveis, ambas nomeadas . A variável `temp` local sombreia a variável `temp` membro `p`quando acessada de dentro de seu próprio procedimento . No entanto, a `MyClass` palavra-chave ignora o sombreamento e acessa a variável membro.  
  
 ![Gráfico que mostra sombra através do escopo.](./media/shadowing/shadow-scope-diagram.gif)
  
 Para um exemplo de sombreamento através do escopo, consulte [Como: Ocultar uma variável com o mesmo nome da sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Sombreamento através da herança  
 Se uma classe derivada redefinir um elemento de programação herdado de uma classe base, o elemento de redefinição sombreia o elemento original. Você pode sombrear qualquer tipo de elemento declarado, ou conjunto de elementos sobrecarregados, com qualquer outro tipo. Por exemplo, `Integer` uma variável `Function` pode sombreá-lo. Se você sombrear um procedimento com outro procedimento, você pode usar uma lista de parâmetros diferente e um tipo de retorno diferente.  
  
 A ilustração a `b` seguir mostra uma `d` classe base `b`e uma classe derivada que herda de . A classe base define `proc`um procedimento chamado , e a classe derivada sombreia-a com outro procedimento de mesmo nome. A `Call` primeira declaração acessa o sombreamento `proc` na classe derivada. No entanto, a `MyBase` palavra-chave ignora o sombreamento e acessa o procedimento sombreado na classe base.  
  
 ![Diagrama gráfico de sombreamento através da herança](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Para um exemplo de sombreamento através da herança, consulte [Como: Ocultar uma Variável com o mesmo Nome da Sua Variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) e [Como: Ocultar uma Variável Herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Nível de sombreamento e acesso  
 O elemento de sombreamento nem sempre é acessível a partir do código usando a classe derivada. Por exemplo, pode ser `Private`declarado . Nesse caso, o sombreamento é derrotado e o compilador resolve qualquer referência ao mesmo elemento que teria se não houvesse sombra. Este elemento é o elemento acessível que menos derivacional passos para trás da classe de sombreamento. Se o elemento sombreado for um procedimento, a resolução será a versão mais acessível com o mesmo nome, lista de parâmetros e tipo de retorno.  
  
 O exemplo a seguir mostra uma hierarquia de herança de três classes. Cada classe define `Sub` `display`um procedimento , e cada `display` classe derivada sombreia o procedimento em sua classe base.  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 No exemplo anterior, as `secondClass` sombras `display` da `Private` classe derivada com um procedimento. Quando `callDisplay` o `display` `secondClass`módulo é chamado, `secondClass` o código de `display` chamada está fora e, portanto, não pode acessar o procedimento privado. O sombreamento é derrotado, e o compilador resolve `display` a referência ao procedimento de classe base.  
  
 No entanto, a `thirdClass` classe `display` `Public`derivada declara como `callDisplay` , para que o código em possa acessá-lo.  
  
## <a name="shadowing-and-overriding"></a>Sombreamento e Substituição  
 Não confunda sombra com sobrepor. Ambos são usados quando uma classe derivada herda de uma classe base, e ambos redefinem um elemento declarado com outro. Mas há diferenças significativas entre os dois. Para uma comparação, consulte [Diferenças entre sombra e substituição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Sombreamento e Sobrecarga  
 Se você sombrear o mesmo elemento de classe base com mais de um elemento em sua classe derivada, os elementos de sombra tornam-se versões sobrecarregadas desse elemento. Para obter mais informações, consulte [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Acessando um elemento sombreado  
 Quando você acessa um elemento de uma classe derivada, você normalmente o faz através `Me` da instância atual dessa classe derivada, qualificando o nome do elemento com a palavra-chave. Se sua classe derivada sombrear o elemento na classe base, você pode `MyBase` acessar o elemento de classe base qualificando-o com a palavra-chave.  
  
 Para um exemplo de acesso a um elemento sombreado, consulte [Como: Acessar uma Variável Oculta por uma Classe Derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Declaração da Variável Objeto  
 A forma como você cria a variável objeto também pode afetar se a classe derivada acessa um elemento de sombra ou o elemento sombreado. O exemplo a seguir cria dois objetos de uma classe derivada, mas um objeto é declarado como a classe base e o outro como a classe derivada.  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 No exemplo anterior, `basObj` a variável é declarada como a classe base. Atribuir um `dervCls` objeto a ele constitui uma conversão de ampliação e, portanto, é válido. No entanto, a classe base não `z` pode acessar a versão de sombreamento da `basObj.z` variável na classe derivada, de modo que o compilador resolve-se com o valor de classe base original.  
  
## <a name="see-also"></a>Confira também

- [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções básicas de herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
