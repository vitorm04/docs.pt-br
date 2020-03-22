---
title: Noções básicas de herança
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400879"
---
# <a name="inheritance-basics-visual-basic"></a>Noções básicas de herança (Visual Basic)

A `Inherits` declaração é usada para declarar uma nova classe, chamada *de classe derivada,* baseada em uma classe existente, conhecida como *classe base.* As classes derivadas herdam, e podem estender, as propriedades, métodos, eventos, campos e constantes definidas na classe base. A seção a seguir descreve algumas das regras para herança, e os modificadores que você pode usar para alterar a forma como as classes herdam ou são herdadas:

- Por padrão, todas as classes são `NotInheritable` hereditárias, a menos que marcadas com a palavra-chave. As aulas podem herdar de outras classes em seu projeto ou de aulas em outras montagens que seu projeto faz referência.

- Ao contrário das linguagens que permitem herança múltipla, o Visual Basic permite apenas uma herança única nas classes; ou seja, as classes derivadas podem ter apenas uma classe base. Embora a herança múltipla não seja permitida nas classes, as classes podem implementar múltiplas interfaces, que podem efetivamente alcançar os mesmos fins.

- Para evitar expor itens restritos em uma classe base, o tipo de acesso de uma classe derivada deve ser igual ou mais restritivo do que sua classe base. Por exemplo, `Public` uma classe `Friend` não `Private` pode herdar uma ou uma classe, e uma `Friend` classe não pode herdar uma `Private` classe.

## <a name="inheritance-modifiers"></a>Modificadores de herança

O Visual Basic introduz as seguintes instruções de nível de classe e modificadores para apoiar a herança:

- `Inherits`declaração — Especifica a classe base.

- `NotInheritable`modificador — Impede que os programadores usem a classe como classe base.

- `MustInherit`modificador — Especifica que a classe destina-se a ser usada apenas como classe base. As `MustInherit` instâncias das classes não podem ser criadas diretamente; eles só podem ser criados como instâncias de classe base de uma classe derivada. (Outras linguagens de programação, como C++ e C#, usam o termo *classe abstrata* para descrever tal classe.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Sobrepondo propriedades e métodos em classes derivadas

Por padrão, uma classe derivada herda propriedades e métodos de sua classe base. Se uma propriedade ou método herdado tiver que se comportar de forma diferente na classe derivada, ele pode ser *substituído*. Ou seja, você pode definir uma nova implementação do método na classe derivada. Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:

- `Overridable`— Permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.

- `Overrides`— Substitui `Overridable` uma propriedade ou método definido na classe base.

- `NotOverridable`— Impede que uma propriedade ou método seja substituído em uma classe herdada. Por padrão, `Public` os `NotOverridable`métodos são .

- `MustOverride`— Requer que uma classe derivada sobreponha a propriedade ou o método. Quando `MustOverride` a palavra-chave é usada, a `Sub`definição `Function`do `Property` método consiste apenas na , ou declaração. Não são permitidas outras declarações, `End Function` e especificamente não há ou `End Sub` declaração. `MustOverride`métodos devem ser `MustInherit` declarados em classes.

Suponha que você queira definir classes para lidar com folha de pagamento. Você pode definir `Payroll` uma classe `RunPayroll` genérica que contém um método que calcula a folha de pagamento para uma semana típica. Você poderia `Payroll` então usar como uma classe `BonusPayroll` base para uma classe mais especializada, que poderia ser usado na distribuição de bônus de funcionários.

A `BonusPayroll` classe pode herdar, `PayEmployee` e substituir, `Payroll` o método definido na classe base.

O exemplo a seguir define `Payroll,` uma classe base, e uma classe derivada, `BonusPayroll`que substitui um método herdado, `PayEmployee`. Um `RunPayroll`procedimento, cria e `Payroll` depois passa `BonusPayroll` um objeto `Pay`e um objeto `PayEmployee` para uma função, que executa o método de ambos os objetos.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>A palavra-chave MyBase

A `MyBase` palavra-chave se comporta como uma variável de objeto que se refere à classe base da instância atual de uma classe. `MyBase`é freqüentemente usado para acessar membros da classe base que são substituídos ou sombreados em uma classe derivada. Em particular, `MyBase.New` é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivado.

Por exemplo, suponha que você esteja projetando uma classe derivada que substitui um método herdado da classe base. O método substituído pode chamar o método na classe base e modificar o valor de retorno conforme mostrado no fragmento de código a seguir:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

A lista a seguir descreve `MyBase`restrições ao uso:

- `MyBase`refere-se à classe base imediata e seus membros herdados. Não pode ser `Private` usado para acessar membros da classe.

- `MyBase`é uma palavra-chave, não um objeto real. `MyBase`não pode ser atribuído a uma variável, passado `Is` para procedimentos ou usado em uma comparação.

- O método `MyBase` que se qualifica não precisa ser definido na classe base imediata; em vez disso, pode ser definida em uma classe base herdada indiretamente. Para que uma referência `MyBase` qualificada para compilar corretamente, alguma classe base deve conter um método que corresponda ao nome e aos tipos de parâmetros que aparecem na chamada.

- Você não `MyBase` pode `MustOverride` usar para chamar métodos de classe base.

- `MyBase`não pode ser usado para se qualificar. Portanto, o seguinte código não é válido:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`não pode ser usado em módulos.

- `MyBase`não pode ser usado para acessar `Friend` membros da classe base que são marcados como se a classe base estivesse em uma montagem diferente.

Para obter mais informações e outro exemplo, [consulte Como: Acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>A palavra-chave MyClass

A `MyClass` palavra-chave se comporta como uma variável de objeto que se refere à instância atual de uma classe como originalmente implementada. `MyClass`se `Me`assemelha, mas cada método `MyClass` e chamada de propriedade é tratado como se o método ou propriedade não fossem [superáveis](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Portanto, o método ou propriedade não é afetado pela substituição em uma classe derivada.

- `MyClass`é uma palavra-chave, não um objeto real. `MyClass`não pode ser atribuído a uma variável, passado `Is` para procedimentos ou usado em uma comparação.

- `MyClass`refere-se à classe que contém e seus membros herdados.

- `MyClass`pode ser usado como `Shared` um qualificador para membros.

- `MyClass`não pode ser `Shared` usado dentro de um método, mas pode ser usado dentro de um método de instância para acessar um membro compartilhado de uma classe.

- `MyClass`não pode ser usado em módulos padrão.

- `MyClass`pode ser usado para qualificar um método definido em uma classe base e que não tem nenhuma implementação do método fornecido nessa classe. Tal referência tem o `MyBase.`mesmo significado *de Método*.

O exemplo a `Me` `MyClass`seguir se compara e .

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

Mesmo `derivedClass` que `testMethod`seja `MyClass` sobreposta, a palavra-chave em `useMyClass` anula os efeitos da substituição, e o `testMethod`compilador resolve a chamada para a versão de classe base de .

## <a name="see-also"></a>Confira também

- [Instrução Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
