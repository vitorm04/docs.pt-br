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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350830"
---
# <a name="inheritance-basics-visual-basic"></a>Noções básicas de herança (Visual Basic)

A instrução `Inherits` é usada para declarar uma nova classe, chamada de *classe derivada*, com base em uma classe existente, conhecida como *classe base*. As classes derivadas herdam e podem estender, as propriedades, os métodos, os eventos, os campos e as constantes definidas na classe base. A seção a seguir descreve algumas das regras de herança e os modificadores que você pode usar para alterar a forma como as classes herdam ou são herdadas:

- Por padrão, todas as classes são herdáveis, a menos que sejam marcadas com a palavra-chave `NotInheritable`. Classes podem herdar de outras classes em seu projeto ou de classes em outros assemblies que seu projeto referencia.

- Ao contrário de linguagens que permitem várias heranças, Visual Basic permite apenas uma única herança em classes; ou seja, as classes derivadas podem ter apenas uma classe base. Embora várias heranças não sejam permitidas em classes, as classes podem implementar várias interfaces, o que pode efetivamente atingir as mesmas extremidades.

- Para evitar a exposição de itens restritos em uma classe base, o tipo de acesso de uma classe derivada deve ser igual ou mais restritivo do que sua classe base. Por exemplo, uma classe `Public` não pode herdar uma classe `Friend` ou `Private`, e uma classe `Friend` não pode herdar uma classe `Private`.

## <a name="inheritance-modifiers"></a>Modificadores de herança

Visual Basic apresenta as seguintes instruções e modificadores de nível de classe para dar suporte à herança:

- instrução `Inherits` — especifica a classe base.

- `NotInheritable` modificador — impede que os programadores usem a classe como uma classe base.

- `MustInherit` modificador — especifica que a classe destina-se ao uso apenas como uma classe base. Instâncias de `MustInherit` classes não podem ser criadas diretamente; Eles só podem ser criados como instâncias de classe base de uma classe derivada. (Outras linguagens de programação, C++ como C#e, usam a *classe abstract* de termo para descrever tal classe.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Substituindo propriedades e métodos em classes derivadas

Por padrão, uma classe derivada herda propriedades e métodos de sua classe base. Se uma propriedade ou método herdado tiver que se comportar de forma diferente na classe derivada, ela poderá ser *substituída*. Ou seja, você pode definir uma nova implementação do método na classe derivada. Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:

- `Overridable` — permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.

- `Overrides` — substitui uma propriedade `Overridable` ou método definido na classe base.

- `NotOverridable` — impede que uma propriedade ou método seja substituído em uma classe herdeira. Por padrão, os métodos de `Public` são `NotOverridable`.

- `MustOverride` — requer que uma classe derivada substitua a propriedade ou o método. Quando a palavra-chave `MustOverride` é usada, a definição do método consiste apenas na instrução `Sub`, `Function`ou `Property`. Nenhuma outra instrução é permitida e, especificamente, não há nenhuma declaração de `End Sub` ou `End Function`. os métodos de `MustOverride` devem ser declarados em classes `MustInherit`.

Suponha que você queira definir classes para lidar com a folha de pagamento. Você pode definir uma classe de `Payroll` genérica que contém um método `RunPayroll` que calcula a folha de pagamento de uma semana típica. Em seguida, você poderia usar `Payroll` como uma classe base para uma classe de `BonusPayroll` mais especializada, que poderia ser usada ao distribuir bônus do funcionário.

A classe `BonusPayroll` pode herdar e substituir o método `PayEmployee` definido na classe base `Payroll`.

O exemplo a seguir define uma classe base, `Payroll,` e uma classe derivada, `BonusPayroll`, que substitui um método herdado, `PayEmployee`. Um procedimento, `RunPayroll`, cria e, em seguida, passa um objeto `Payroll` e um objeto `BonusPayroll` para uma função, `Pay`, que executa o método `PayEmployee` de ambos os objetos.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>A palavra-chave MyBase

A palavra-chave `MyBase` se comporta como uma variável de objeto que se refere à classe base da instância atual de uma classe. `MyBase` é frequentemente usado para acessar membros da classe base que são substituídos ou sombreados em uma classe derivada. Em particular, `MyBase.New` é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivada.

Por exemplo, suponha que você esteja criando uma classe derivada que substitua um método herdado da classe base. O método substituído pode chamar o método na classe base e modificar o valor de retorno, conforme mostrado no fragmento de código a seguir:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

A lista a seguir descreve as restrições sobre como usar `MyBase`:

- `MyBase` refere-se à classe base imediata e seus membros herdados. Ele não pode ser usado para acessar membros de `Private` na classe.

- `MyBase` é uma palavra-chave, não um objeto real. `MyBase` não pode ser atribuída a uma variável, passada para procedimentos ou usada em uma comparação de `Is`.

- O método que `MyBase` qualificado não precisa ser definido na classe base imediata; em vez disso, ele pode ser definido em uma classe base indiretamente herdada. Para que uma referência qualificada pelo `MyBase` seja compilada corretamente, uma classe base deve conter um método que corresponda ao nome e aos tipos de parâmetros que aparecem na chamada.

- Você não pode usar `MyBase` para chamar `MustOverride` métodos de classe base.

- `MyBase` não pode ser usado para se qualificar. Portanto, o código a seguir não é válido:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase` não pode ser usado em módulos.

- `MyBase` não pode ser usado para acessar membros da classe base que estão marcados como `Friend` se a classe base estiver em um assembly diferente.

Para obter mais informações e outro exemplo, consulte [como: acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>A palavra-chave MyClass

A palavra-chave `MyClass` se comporta como uma variável de objeto que se refere à instância atual de uma classe como originalmente implementada. `MyClass` se assemelha a `Me`, mas cada chamada de método e propriedade em `MyClass` é tratada como se o método ou a propriedade fossem [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Portanto, o método ou a propriedade não é afetada pela substituição em uma classe derivada.

- `MyClass` é uma palavra-chave, não um objeto real. `MyClass` não pode ser atribuída a uma variável, passada para procedimentos ou usada em uma comparação de `Is`.

- `MyClass` refere-se à classe que a contém e seus membros herdados.

- `MyClass` pode ser usado como um qualificador para membros de `Shared`.

- `MyClass` não pode ser usada dentro de um método `Shared`, mas pode ser usada dentro de um método de instância para acessar um membro compartilhado de uma classe.

- `MyClass` não pode ser usado em módulos padrão.

- `MyClass` pode ser usado para qualificar um método que é definido em uma classe base e que não tem implementação do método fornecido nessa classe. Essa referência tem o mesmo significado que `MyBase.`*método*.

O exemplo a seguir compara `Me` e `MyClass`.

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

Embora `derivedClass` substitui `testMethod`, a palavra-chave `MyClass` em `useMyClass` invalidará os efeitos da substituição e o compilador resolve a chamada para a versão da classe base do `testMethod`.

## <a name="see-also"></a>Consulte também

- [Instrução Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
