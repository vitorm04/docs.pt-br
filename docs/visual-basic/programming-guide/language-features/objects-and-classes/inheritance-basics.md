---
title: Noções básicas de herança (Visual Basic)
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
ms.openlocfilehash: ae6b53db3a2cdcefa2b05d68ed953c5e17b279dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551781"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="c73c4-102">Noções básicas de herança (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c73c4-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="c73c4-103">O `Inherits` instrução é usada para declarar uma nova classe chamada um *classe derivada*, com base em uma classe existente, conhecida como um *classe base*.</span><span class="sxs-lookup"><span data-stu-id="c73c4-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="c73c4-104">Classes derivadas herdam e podem estender, propriedades, métodos, eventos, campos e constantes definidas na classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="c73c4-105">A seção a seguir descreve algumas das regras de herança, e os modificadores que você pode usar para alterar as classes de forma herdam ou são herdados:</span><span class="sxs-lookup"><span data-stu-id="c73c4-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="c73c4-106">Por padrão, todas as classes são herdadas, a menos que marcados com o `NotInheritable` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c73c4-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="c73c4-107">As classes podem herdar de outras classes em seu projeto ou de classes em outros assemblies que faz referência a seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c73c4-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="c73c4-108">Ao contrário de linguagens que permitem a herança múltipla, o Visual Basic permite somente a herança única em classes; ou seja, classes derivadas podem ter apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="c73c4-109">Embora a herança múltipla não é permitida em classes, classes podem implementar várias interfaces, o que podem ser feito efetivamente o mesmo termina.</span><span class="sxs-lookup"><span data-stu-id="c73c4-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="c73c4-110">Para evitar a exposição restritos itens em uma classe base, o tipo de acesso de uma classe derivada deve ser igual ou mais restritivo do que sua classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="c73c4-111">Por exemplo, uma `Public` classe não pode herdar uma `Friend` ou um `Private` classe e uma `Friend` classe não pode herdar um `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="c73c4-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="c73c4-112">Modificadores de herança</span><span class="sxs-lookup"><span data-stu-id="c73c4-112">Inheritance Modifiers</span></span>  
 <span data-ttu-id="c73c4-113">Visual Basic apresenta as seguintes instruções de nível de classe e modificadores para dar suporte à herança:</span><span class="sxs-lookup"><span data-stu-id="c73c4-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="c73c4-114">`Inherits` instrução — Especifica a classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="c73c4-115">`NotInheritable` modificador — impede que os programadores usando a classe como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="c73c4-116">`MustInherit` modificador — Especifica que a classe é destinada para uso como apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="c73c4-117">Instâncias de `MustInherit` classes não podem ser criadas diretamente; elas só podem ser criadas instâncias de classe como a base de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="c73c4-118">(Outras linguagens de programação, como C++ e C#, use o termo *classe abstrata* para descrever essa classe.)</span><span class="sxs-lookup"><span data-stu-id="c73c4-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="c73c4-119">Substituindo propriedades e métodos em Classes derivadas</span><span class="sxs-lookup"><span data-stu-id="c73c4-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="c73c4-120">Por padrão, uma classe derivada herda propriedades e métodos de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="c73c4-121">Se uma propriedade ou método herdado deve se comportar de maneira diferente na classe derivada pode ser *substituído*.</span><span class="sxs-lookup"><span data-stu-id="c73c4-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="c73c4-122">Ou seja, você pode definir uma nova implementação do método na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="c73c4-123">Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:</span><span class="sxs-lookup"><span data-stu-id="c73c4-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="c73c4-124">`Overridable` — Permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="c73c4-125">`Overrides` — Substitui uma `Overridable` propriedade ou método definido na classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="c73c4-126">`NotOverridable` — Impede que uma propriedade ou método que está sendo substituído em uma classe herdada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="c73c4-127">Por padrão, `Public` métodos são `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="c73c4-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="c73c4-128">`MustOverride` — Exige que uma classe derivada substituem o método ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="c73c4-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="c73c4-129">Quando o `MustOverride` palavra-chave é usada, a definição do método consiste apenas o `Sub`, `Function`, ou `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="c73c4-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="c73c4-130">Nenhuma outra instrução é permitidas e especificamente não há nenhuma `End Sub` ou `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="c73c4-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="c73c4-131">`MustOverride` os métodos devem ser declarados em `MustInherit` classes.</span><span class="sxs-lookup"><span data-stu-id="c73c4-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="c73c4-132">Suponha que você queira definir classes para tratar da folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="c73c4-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="c73c4-133">Você pode definir um genérico `Payroll` classe que contém um `RunPayroll` método que calcula o pagamento de uma semana típica.</span><span class="sxs-lookup"><span data-stu-id="c73c4-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="c73c4-134">Você pode usar `Payroll` como uma classe base para um mais especializadas `BonusPayroll` classe, que pode ser usada ao distribuir bônus aos funcionários.</span><span class="sxs-lookup"><span data-stu-id="c73c4-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="c73c4-135">O `BonusPayroll` classe pode herdar e substituir, o `PayEmployee` método definido na base de `Payroll` classe.</span><span class="sxs-lookup"><span data-stu-id="c73c4-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="c73c4-136">O exemplo a seguir define uma classe base, `Payroll,` e uma classe derivada, `BonusPayroll`, que substitui um método herdado, `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="c73c4-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="c73c4-137">Um procedimento, `RunPayroll`, cria e, em seguida, passa uma `Payroll` objeto e uma `BonusPayroll` objeto para uma função `Pay`, que executa o `PayEmployee` método dos dois objetos.</span><span class="sxs-lookup"><span data-stu-id="c73c4-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="c73c4-138">A palavra-chave MyBase</span><span class="sxs-lookup"><span data-stu-id="c73c4-138">The MyBase Keyword</span></span>  
 <span data-ttu-id="c73c4-139">O `MyBase` palavra-chave se comporta como uma variável de objeto que faz referência à classe base da instância atual de uma classe.</span><span class="sxs-lookup"><span data-stu-id="c73c4-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="c73c4-140">`MyBase` é frequentemente usado para acessar membros de classe base que são substituídos ou sombreados em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="c73c4-141">Em particular, `MyBase.New` é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="c73c4-142">Por exemplo, suponha que você está criando uma classe derivada que substitui um método herdado da classe base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="c73c4-143">O método substituído pode chamar o método na classe base e modifique o valor de retorno, conforme mostrado no seguinte fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="c73c4-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 <span data-ttu-id="c73c4-144">A lista a seguir descreve as restrições sobre como usar `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="c73c4-144">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="c73c4-145">`MyBase` refere-se a classe base imediata e seus membros herdados.</span><span class="sxs-lookup"><span data-stu-id="c73c4-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="c73c4-146">Ele não pode ser usado para acessar `Private` os membros da classe.</span><span class="sxs-lookup"><span data-stu-id="c73c4-146">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="c73c4-147">`MyBase` é uma palavra-chave, não um objeto real.</span><span class="sxs-lookup"><span data-stu-id="c73c4-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="c73c4-148">`MyBase` não pode ser atribuído a uma variável, passados a procedimentos ou usados em um `Is` comparação.</span><span class="sxs-lookup"><span data-stu-id="c73c4-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="c73c4-149">O método que `MyBase` qualifica não precisa ser definido na classe base imediata; em vez disso, podem ser definido em uma classe base indiretamente herdada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="c73c4-150">Para que uma referência qualificada pelo `MyBase` sejam compilados corretamente, alguma classe base deve conter um método correspondente, o nome e os tipos de parâmetros que aparecem na chamada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="c73c4-151">Não é possível usar `MyBase` chamar `MustOverride` métodos da classe de base.</span><span class="sxs-lookup"><span data-stu-id="c73c4-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="c73c4-152">`MyBase` não pode ser usado para qualificar em si.</span><span class="sxs-lookup"><span data-stu-id="c73c4-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="c73c4-153">Portanto, o código a seguir não é válido:</span><span class="sxs-lookup"><span data-stu-id="c73c4-153">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="c73c4-154">`MyBase` não pode ser usado em módulos.</span><span class="sxs-lookup"><span data-stu-id="c73c4-154">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="c73c4-155">`MyBase` não pode ser usado para acessar membros de classe base que são marcados como `Friend` se a classe base está em um assembly diferente.</span><span class="sxs-lookup"><span data-stu-id="c73c4-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="c73c4-156">Para obter mais informações e outro exemplo, consulte [como: Acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="c73c4-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="c73c4-157">A palavra-chave MyClass</span><span class="sxs-lookup"><span data-stu-id="c73c4-157">The MyClass Keyword</span></span>  
 <span data-ttu-id="c73c4-158">O `MyClass` palavra-chave se comporta como uma variável de objeto que se refere à instância atual de uma classe como originalmente implementada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="c73c4-159">`MyClass` é semelhante a `Me`, mas cada método e propriedade chamar no `MyClass` é tratada como se o método ou propriedade fossem [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="c73c4-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="c73c4-160">Portanto, o método ou propriedade não é afetada por meio da substituição em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c73c4-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="c73c4-161">`MyClass` é uma palavra-chave, não um objeto real.</span><span class="sxs-lookup"><span data-stu-id="c73c4-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="c73c4-162">`MyClass` não pode ser atribuído a uma variável, passados a procedimentos ou usados em um `Is` comparação.</span><span class="sxs-lookup"><span data-stu-id="c73c4-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="c73c4-163">`MyClass` refere-se a classe recipiente e seus membros herdados.</span><span class="sxs-lookup"><span data-stu-id="c73c4-163">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="c73c4-164">`MyClass` pode ser usado como um qualificador para `Shared` membros.</span><span class="sxs-lookup"><span data-stu-id="c73c4-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="c73c4-165">`MyClass` não pode ser usado dentro de um `Shared` método, mas pode ser usado dentro de um método de instância para acessar um membro compartilhado de uma classe.</span><span class="sxs-lookup"><span data-stu-id="c73c4-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="c73c4-166">`MyClass` não pode ser usado em módulos padrão.</span><span class="sxs-lookup"><span data-stu-id="c73c4-166">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="c73c4-167">`MyClass` pode ser usado para qualificar um método que é definido em uma classe base e que não tem nenhuma implementação do método fornecido nessa classe.</span><span class="sxs-lookup"><span data-stu-id="c73c4-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="c73c4-168">Essa referência tem o mesmo significado que `MyBase.` *método*.</span><span class="sxs-lookup"><span data-stu-id="c73c4-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="c73c4-169">O exemplo a seguir compara `Me` e `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="c73c4-169">The following example compares `Me` and `MyClass`.</span></span>  
  
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
  
 <span data-ttu-id="c73c4-170">Embora `derivedClass` substituições `testMethod`, o `MyClass` palavra-chave na `useMyClass` anula os efeitos de substituição e o compilador resolve a chamada para a versão da classe base do `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="c73c4-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73c4-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c73c4-171">See also</span></span>
- [<span data-ttu-id="c73c4-172">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="c73c4-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="c73c4-173">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="c73c4-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
