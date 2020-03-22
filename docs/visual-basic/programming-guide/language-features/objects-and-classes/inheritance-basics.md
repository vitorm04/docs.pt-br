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
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="cc2aa-102">Noções básicas de herança (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc2aa-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="cc2aa-103">A `Inherits` declaração é usada para declarar uma nova classe, chamada *de classe derivada,* baseada em uma classe existente, conhecida como *classe base.*</span><span class="sxs-lookup"><span data-stu-id="cc2aa-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="cc2aa-104">As classes derivadas herdam, e podem estender, as propriedades, métodos, eventos, campos e constantes definidas na classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="cc2aa-105">A seção a seguir descreve algumas das regras para herança, e os modificadores que você pode usar para alterar a forma como as classes herdam ou são herdadas:</span><span class="sxs-lookup"><span data-stu-id="cc2aa-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="cc2aa-106">Por padrão, todas as classes são `NotInheritable` hereditárias, a menos que marcadas com a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="cc2aa-107">As aulas podem herdar de outras classes em seu projeto ou de aulas em outras montagens que seu projeto faz referência.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="cc2aa-108">Ao contrário das linguagens que permitem herança múltipla, o Visual Basic permite apenas uma herança única nas classes; ou seja, as classes derivadas podem ter apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="cc2aa-109">Embora a herança múltipla não seja permitida nas classes, as classes podem implementar múltiplas interfaces, que podem efetivamente alcançar os mesmos fins.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="cc2aa-110">Para evitar expor itens restritos em uma classe base, o tipo de acesso de uma classe derivada deve ser igual ou mais restritivo do que sua classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="cc2aa-111">Por exemplo, `Public` uma classe `Friend` não `Private` pode herdar uma ou uma classe, e uma `Friend` classe não pode herdar uma `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="cc2aa-112">Modificadores de herança</span><span class="sxs-lookup"><span data-stu-id="cc2aa-112">Inheritance Modifiers</span></span>

<span data-ttu-id="cc2aa-113">O Visual Basic introduz as seguintes instruções de nível de classe e modificadores para apoiar a herança:</span><span class="sxs-lookup"><span data-stu-id="cc2aa-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="cc2aa-114">`Inherits`declaração — Especifica a classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="cc2aa-115">`NotInheritable`modificador — Impede que os programadores usem a classe como classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="cc2aa-116">`MustInherit`modificador — Especifica que a classe destina-se a ser usada apenas como classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="cc2aa-117">As `MustInherit` instâncias das classes não podem ser criadas diretamente; eles só podem ser criados como instâncias de classe base de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="cc2aa-118">(Outras linguagens de programação, como C++ e C#, usam o termo *classe abstrata* para descrever tal classe.)</span><span class="sxs-lookup"><span data-stu-id="cc2aa-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="cc2aa-119">Sobrepondo propriedades e métodos em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="cc2aa-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="cc2aa-120">Por padrão, uma classe derivada herda propriedades e métodos de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="cc2aa-121">Se uma propriedade ou método herdado tiver que se comportar de forma diferente na classe derivada, ele pode ser *substituído*.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="cc2aa-122">Ou seja, você pode definir uma nova implementação do método na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="cc2aa-123">Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:</span><span class="sxs-lookup"><span data-stu-id="cc2aa-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="cc2aa-124">`Overridable`— Permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="cc2aa-125">`Overrides`— Substitui `Overridable` uma propriedade ou método definido na classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="cc2aa-126">`NotOverridable`— Impede que uma propriedade ou método seja substituído em uma classe herdada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="cc2aa-127">Por padrão, `Public` os `NotOverridable`métodos são .</span><span class="sxs-lookup"><span data-stu-id="cc2aa-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="cc2aa-128">`MustOverride`— Requer que uma classe derivada sobreponha a propriedade ou o método.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="cc2aa-129">Quando `MustOverride` a palavra-chave é usada, a `Sub`definição `Function`do `Property` método consiste apenas na , ou declaração.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="cc2aa-130">Não são permitidas outras declarações, `End Function` e especificamente não há ou `End Sub` declaração.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="cc2aa-131">`MustOverride`métodos devem ser `MustInherit` declarados em classes.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="cc2aa-132">Suponha que você queira definir classes para lidar com folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="cc2aa-133">Você pode definir `Payroll` uma classe `RunPayroll` genérica que contém um método que calcula a folha de pagamento para uma semana típica.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="cc2aa-134">Você poderia `Payroll` então usar como uma classe `BonusPayroll` base para uma classe mais especializada, que poderia ser usado na distribuição de bônus de funcionários.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="cc2aa-135">A `BonusPayroll` classe pode herdar, `PayEmployee` e substituir, `Payroll` o método definido na classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="cc2aa-136">O exemplo a seguir define `Payroll,` uma classe base, e uma classe derivada, `BonusPayroll`que substitui um método herdado, `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="cc2aa-137">Um `RunPayroll`procedimento, cria e `Payroll` depois passa `BonusPayroll` um objeto `Pay`e um objeto `PayEmployee` para uma função, que executa o método de ambos os objetos.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="cc2aa-138">A palavra-chave MyBase</span><span class="sxs-lookup"><span data-stu-id="cc2aa-138">The MyBase Keyword</span></span>

<span data-ttu-id="cc2aa-139">A `MyBase` palavra-chave se comporta como uma variável de objeto que se refere à classe base da instância atual de uma classe.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="cc2aa-140">`MyBase`é freqüentemente usado para acessar membros da classe base que são substituídos ou sombreados em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="cc2aa-141">Em particular, `MyBase.New` é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivado.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="cc2aa-142">Por exemplo, suponha que você esteja projetando uma classe derivada que substitui um método herdado da classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="cc2aa-143">O método substituído pode chamar o método na classe base e modificar o valor de retorno conforme mostrado no fragmento de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="cc2aa-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="cc2aa-144">A lista a seguir descreve `MyBase`restrições ao uso:</span><span class="sxs-lookup"><span data-stu-id="cc2aa-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="cc2aa-145">`MyBase`refere-se à classe base imediata e seus membros herdados.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="cc2aa-146">Não pode ser `Private` usado para acessar membros da classe.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="cc2aa-147">`MyBase`é uma palavra-chave, não um objeto real.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="cc2aa-148">`MyBase`não pode ser atribuído a uma variável, passado `Is` para procedimentos ou usado em uma comparação.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="cc2aa-149">O método `MyBase` que se qualifica não precisa ser definido na classe base imediata; em vez disso, pode ser definida em uma classe base herdada indiretamente.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="cc2aa-150">Para que uma referência `MyBase` qualificada para compilar corretamente, alguma classe base deve conter um método que corresponda ao nome e aos tipos de parâmetros que aparecem na chamada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="cc2aa-151">Você não `MyBase` pode `MustOverride` usar para chamar métodos de classe base.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="cc2aa-152">`MyBase`não pode ser usado para se qualificar.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="cc2aa-153">Portanto, o seguinte código não é válido:</span><span class="sxs-lookup"><span data-stu-id="cc2aa-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="cc2aa-154">`MyBase`não pode ser usado em módulos.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="cc2aa-155">`MyBase`não pode ser usado para acessar `Friend` membros da classe base que são marcados como se a classe base estivesse em uma montagem diferente.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="cc2aa-156">Para obter mais informações e outro exemplo, [consulte Como: Acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="cc2aa-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="cc2aa-157">A palavra-chave MyClass</span><span class="sxs-lookup"><span data-stu-id="cc2aa-157">The MyClass Keyword</span></span>

<span data-ttu-id="cc2aa-158">A `MyClass` palavra-chave se comporta como uma variável de objeto que se refere à instância atual de uma classe como originalmente implementada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="cc2aa-159">`MyClass`se `Me`assemelha, mas cada método `MyClass` e chamada de propriedade é tratado como se o método ou propriedade não fossem [superáveis](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="cc2aa-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="cc2aa-160">Portanto, o método ou propriedade não é afetado pela substituição em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="cc2aa-161">`MyClass`é uma palavra-chave, não um objeto real.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="cc2aa-162">`MyClass`não pode ser atribuído a uma variável, passado `Is` para procedimentos ou usado em uma comparação.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="cc2aa-163">`MyClass`refere-se à classe que contém e seus membros herdados.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="cc2aa-164">`MyClass`pode ser usado como `Shared` um qualificador para membros.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="cc2aa-165">`MyClass`não pode ser `Shared` usado dentro de um método, mas pode ser usado dentro de um método de instância para acessar um membro compartilhado de uma classe.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="cc2aa-166">`MyClass`não pode ser usado em módulos padrão.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="cc2aa-167">`MyClass`pode ser usado para qualificar um método definido em uma classe base e que não tem nenhuma implementação do método fornecido nessa classe.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="cc2aa-168">Tal referência tem o `MyBase.`mesmo significado *de Método*.</span><span class="sxs-lookup"><span data-stu-id="cc2aa-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="cc2aa-169">O exemplo a `Me` `MyClass`seguir se compara e .</span><span class="sxs-lookup"><span data-stu-id="cc2aa-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="cc2aa-170">Mesmo `derivedClass` que `testMethod`seja `MyClass` sobreposta, a palavra-chave em `useMyClass` anula os efeitos da substituição, e o `testMethod`compilador resolve a chamada para a versão de classe base de .</span><span class="sxs-lookup"><span data-stu-id="cc2aa-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc2aa-171">Confira também</span><span class="sxs-lookup"><span data-stu-id="cc2aa-171">See also</span></span>

- [<span data-ttu-id="cc2aa-172">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="cc2aa-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="cc2aa-173">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="cc2aa-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
