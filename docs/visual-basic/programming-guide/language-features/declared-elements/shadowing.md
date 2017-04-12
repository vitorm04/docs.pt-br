---
title: Sombreamento no Visual Basic | Documentos do Microsoft
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
- inheritance, shadowing
- overriding, and shadowing
- shadowing
- duplicate names
- shadowing, by inheritance
- declared elements, referencing
- shadowing, by scope
- declared elements, hiding
- naming conflicts, shadowing
- declared elements, shadowing
- shadowing, and overriding
- scope, shadowing
- Shadows keyword, about
- objects [Visual Basic], names
- names, shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
caps.latest.revision: 24
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
ms.openlocfilehash: 5f4053de05f0a7a42fccdade1714e08f8eb172e6
ms.lasthandoff: 03/13/2017

---
# <a name="shadowing-in-visual-basic"></a>Sombreamento no Visual Basic
Quando dois elementos de programação compartilham o mesmo nome, um deles pode ocultar, ou *sombra*, outro. Nessa situação, o elemento sombreado não está disponível para referência; em vez disso, quando seu código usa o nome do elemento, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador resolve para o elemento de sombreamento.  
  
## <a name="purpose"></a>Finalidade  
 O objetivo principal do sombreamento é proteger a definição de seus membros de classe. A classe base pode passar por uma mudança que cria um elemento com o mesmo nome que um que já definido. Se isso acontecer, o `Shadows` modificador obriga referências através da sua classe a serem resolvidas ao membro que você definiu, em vez de para o novo elemento de classe base.  
  
## <a name="types-of-shadowing"></a>Tipos de sombreamento  
 Um elemento pode sombrear outro elemento de duas maneiras diferentes. O elemento de sombreamento pode ser declarado dentro uma sub-região da região que contém o elemento sombreado, nesse caso o sombreamento é realizado *através de escopo*. Ou uma classe derivada pode redefinir um membro de uma classe base, em que o sombreamento é feito *por meio da herança*.  
  
### <a name="shadowing-through-scope"></a>Sombreamento através de escopo  
 É possível para elementos de programação no mesmo módulo, classe ou estrutura ter o mesmo nome mas escopo diferente. Quando dois elementos são declarados dessa maneira e o código se refere ao nome que eles compartilham, o elemento com o escopo mais estreito sombreia o outro elemento (escopo de bloco é o menor).  
  
 Por exemplo, um módulo pode definir uma `Public` variável chamada `temp`, e um procedimento dentro do módulo pode declarar uma variável local também denominada `temp`. As referências a `temp` de dentro do procedimento acessam a variável local, enquanto referências a `temp` de fora do procedimento acessam a `Public` variável. Nesse caso, a variável de procedimento `temp` sombreia a variável de módulo `temp`.  
  
 A ilustração a seguir mostra duas variáveis, ambas chamadas `temp`. A variável local `temp` sombreia a variável de membro `temp` quando acessado a partir de seu próprio procedimento `p`. No entanto, o `MyClass` palavra-chave ignora o sombreamento e acessa a variável de membro.  
  
 ![Diagrama gráfico de sombreamento através de escopo](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
Sombreamento através de escopo  
  
 Para obter um exemplo de sombreamento através de escopo, consulte [como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Sombreamento através de herança  
 Se uma classe derivada redefine um elemento de programação herdado de uma classe base, o elemento redefinido sombreia o elemento original. Você pode sombrear qualquer tipo de elemento declarado, ou conjunto de elementos sobrecarregados, com qualquer outro tipo. Por exemplo, um `Integer` variável pode sombrear uma `Function` procedimento. Se você sombrear um procedimento com outro procedimento, você pode usar uma lista de parâmetros e um tipo de retorno diferente.  
  
 A ilustração a seguir mostra uma classe base `b` e uma classe derivada `d` que herda de `b`. A classe base define um procedimento denominado `proc`, e a classe derivada o sombreia com outro procedimento de mesmo nome. A primeira `Call` instrução acessa o sombreamento `proc` na classe derivada. No entanto, o `MyBase` palavra-chave ignora o sombreamento e acessa o procedimento sombreado na classe base.  
  
 ![Diagrama gráfico de sombreamento através de herança](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
Sombreamento através de herança  
  
 Para obter um exemplo de sombreamento através de herança, consulte [como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) e [como: ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Sombreamento e nível de acesso  
 O elemento de sombreamento nem sempre é acessível a partir do código usando a classe derivada. Por exemplo, ele pode ser declarado como `Private`. Nesse caso, sombreamento é desfeito e o compilador resolve qualquer referência ao mesmo elemento que ele teria se tivesse sido sombreado. Esse elemento é o elemento acessível com o menor número derivacionais etapas para trás da classe de sombreamento. Se o elemento sombreado é um procedimento, a resolução é a versão mais acessível com o mesmo nome, a lista de parâmetros e tipo de retorno.  
  
 O exemplo a seguir mostra uma hierarquia de herança de três classes. Cada classe define um `Sub` procedimento `display`, e cada classe derivada sombreia o `display` procedimento em sua classe base.  
  
```  
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
  
 No exemplo anterior, a classe derivada `secondClass` sombras `display` com um `Private` procedimento. Ao módulo `callDisplay` chamadas `display` na `secondClass`, o código de chamada está fora `secondClass` e, portanto, não é possível acessar a privada `display` procedimento. O sombreamento é desfeito e o compilador resolve a referência para a classe base `display` procedimento.  
  
 No entanto, a classe derivada adicional `thirdClass` declara `display` como `Public`, então o código em `callDisplay` pode acessá-lo.  
  
## <a name="shadowing-and-overriding"></a>Sombreamento e sobreposição  
 Não confunda sombreamento com substituição. Ambos são usados quando uma classe derivada herda de uma classe base, e os dois redefinem um elemento declarado com outro. Mas há diferenças significativas entre os dois. Para obter uma comparação, consulte [as diferenças entre sombreamento e substituindo](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Sombreamento e sobrecarga  
 Se você sombrear o mesmo elemento de classe base com mais de um elemento em sua classe derivada, os elementos de sombreamento se tornarão versões sobrecarregadas desse elemento. Para obter mais informações, consulte [sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Acessando um elemento sombreado  
 Quando você acessar um elemento de uma classe derivada, você normalmente o faz até a instância atual da classe derivada, qualificando o nome do elemento com a `Me` palavra-chave. Se sua classe derivada sombreia o elemento na classe base, você pode acessar o elemento da classe base usando o `MyBase` palavra-chave.  
  
 Para obter um exemplo de como acessar um elemento sombreado, consulte [como: acessar uma variável oculta por uma classe derivada de](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Declaração de variável de objeto  
 Como criar a variável de objeto também pode afetar se a classe derivada acessa um elemento de sombreamento ou o elemento sombreado. O exemplo a seguir cria dois objetos de uma classe derivada, mas um objeto é declarado como a classe base e o outro como a classe derivada.  
  
```  
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
  
 No exemplo anterior, a variável `basObj` é declarada como a classe base. Atribuindo uma `dervCls` objeto a ela constitui uma conversão de ampliação e, portanto, é válido. No entanto, a classe base não pode acessar a versão sombreada da variável `z` na classe derivada, então o compilador resolve `basObj.z` para o valor original da classe base.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Conversões entre](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
