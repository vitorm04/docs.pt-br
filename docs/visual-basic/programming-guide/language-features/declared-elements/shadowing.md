---
title: Sombreamento no Visual Basic
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
ms.openlocfilehash: fde6259b67a8d963ed8c30b87c94029fb2658664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656065"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="4675f-102">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4675f-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="4675f-103">Quando dois elementos de programação compartilham o mesmo nome, um deles pode ocultar, ou *sombra*, outro.</span><span class="sxs-lookup"><span data-stu-id="4675f-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="4675f-104">Em tal situação, o elemento sombreado não está disponível para referência; em vez disso, quando seu código usa o nome do elemento, o compilador do Visual Basic resolve para o elemento de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="4675f-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="4675f-105">Finalidade</span><span class="sxs-lookup"><span data-stu-id="4675f-105">Purpose</span></span>  
 <span data-ttu-id="4675f-106">O objetivo principal do sombreamento é proteger a definição de seus membros de classe.</span><span class="sxs-lookup"><span data-stu-id="4675f-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="4675f-107">A classe base pode passar por uma mudança que cria um elemento com o mesmo nome que uma que já definido.</span><span class="sxs-lookup"><span data-stu-id="4675f-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="4675f-108">Se isso acontecer, o `Shadows` modificador obriga referências através da sua classe a ser resolvido para o membro que você definiu, em vez de para o novo elemento de classe base.</span><span class="sxs-lookup"><span data-stu-id="4675f-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="4675f-109">Tipos de sombreamento</span><span class="sxs-lookup"><span data-stu-id="4675f-109">Types of Shadowing</span></span>  
 <span data-ttu-id="4675f-110">Um elemento pode sombrear outro elemento de duas maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="4675f-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="4675f-111">O elemento de sombreamento pode ser declarado dentro uma sub-região da região que contém o elemento sombreado, nesse caso o sombreamento é realizado *através de escopo*.</span><span class="sxs-lookup"><span data-stu-id="4675f-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="4675f-112">Ou uma classe derivada pode redefinir um membro de uma classe base, em que o sombreamento é feito *por meio da herança*.</span><span class="sxs-lookup"><span data-stu-id="4675f-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="4675f-113">Sombreamento através de escopo</span><span class="sxs-lookup"><span data-stu-id="4675f-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="4675f-114">É possível para elementos de programação no mesmo módulo, classe ou estrutura ter o mesmo nome mas escopo diferente.</span><span class="sxs-lookup"><span data-stu-id="4675f-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="4675f-115">Quando dois elementos são declarados dessa maneira e o código se refere ao nome que eles compartilham, o elemento com o escopo mais estreito sombreia o outro elemento (escopo de bloco é o menor).</span><span class="sxs-lookup"><span data-stu-id="4675f-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="4675f-116">Por exemplo, um módulo pode definir um `Public` variável chamada `temp`, e um procedimento dentro do módulo pode declarar uma variável local também denominada `temp`.</span><span class="sxs-lookup"><span data-stu-id="4675f-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="4675f-117">As referências a `temp` de dentro do procedimento acessam a variável local, enquanto referências a `temp` de fora do procedimento acessam o `Public` variável.</span><span class="sxs-lookup"><span data-stu-id="4675f-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="4675f-118">Nesse caso, a variável do procedimento `temp` sombreia a variável de módulo `temp`.</span><span class="sxs-lookup"><span data-stu-id="4675f-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="4675f-119">A ilustração a seguir mostra duas variáveis, ambas chamadas `temp`.</span><span class="sxs-lookup"><span data-stu-id="4675f-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="4675f-120">A variável local `temp` sombreia a variável de membro `temp` quando acessado a partir de seu próprio procedimento `p`.</span><span class="sxs-lookup"><span data-stu-id="4675f-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="4675f-121">No entanto, o `MyClass` palavra-chave ignora o sombreamento e acessa a variável de membro.</span><span class="sxs-lookup"><span data-stu-id="4675f-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 <span data-ttu-id="4675f-122">![Diagrama gráfico de sombreamento através de escopo](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span><span class="sxs-lookup"><span data-stu-id="4675f-122">![Graphic diagram of shadowing through scope](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span></span>  
<span data-ttu-id="4675f-123">Sombreamento através de escopo</span><span class="sxs-lookup"><span data-stu-id="4675f-123">Shadowing through scope</span></span>  
  
 <span data-ttu-id="4675f-124">Para obter um exemplo de sombreamento através de escopo, consulte [como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="4675f-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="4675f-125">Sombreamento através de herança</span><span class="sxs-lookup"><span data-stu-id="4675f-125">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="4675f-126">Se uma classe derivada redefine um elemento de programação herdado de uma classe base, o elemento redefinido sombreia o elemento original.</span><span class="sxs-lookup"><span data-stu-id="4675f-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="4675f-127">Você pode sombrear qualquer tipo de elemento declarado ou conjunto de elementos sobrecarregados, com qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="4675f-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="4675f-128">Por exemplo, um `Integer` variável pode sombrear um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4675f-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="4675f-129">Se você sombrear um procedimento com outro procedimento, você pode usar uma lista de parâmetros diferentes e um tipo de retorno diferente.</span><span class="sxs-lookup"><span data-stu-id="4675f-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="4675f-130">A ilustração a seguir mostra uma classe base `b` e uma classe derivada `d` que herda de `b`.</span><span class="sxs-lookup"><span data-stu-id="4675f-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="4675f-131">A classe base define um procedimento denominado `proc`, e a classe derivada sombreia com outro procedimento de mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4675f-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="4675f-132">A primeira `Call` instrução acessa o sombreamento `proc` na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="4675f-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="4675f-133">No entanto, o `MyBase` palavra-chave ignora o sombreamento e acessa o procedimento sombreado na classe base.</span><span class="sxs-lookup"><span data-stu-id="4675f-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 <span data-ttu-id="4675f-134">![Diagrama gráfico de sombreamento através de herança](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span><span class="sxs-lookup"><span data-stu-id="4675f-134">![Graphic diagram of shadowing through inheritance](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span></span>  
<span data-ttu-id="4675f-135">Sombreamento através de herança</span><span class="sxs-lookup"><span data-stu-id="4675f-135">Shadowing through inheritance</span></span>  
  
 <span data-ttu-id="4675f-136">Para obter um exemplo de sombreamento através de herança, consulte [como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) e [como: ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="4675f-136">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="4675f-137">Sombreamento e nível de acesso</span><span class="sxs-lookup"><span data-stu-id="4675f-137">Shadowing and Access Level</span></span>  
 <span data-ttu-id="4675f-138">O elemento de sombreamento sempre não é acessível a partir do código usando a classe derivada.</span><span class="sxs-lookup"><span data-stu-id="4675f-138">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="4675f-139">Por exemplo, ele pode ser declarado como `Private`.</span><span class="sxs-lookup"><span data-stu-id="4675f-139">For example, it might be declared `Private`.</span></span> <span data-ttu-id="4675f-140">Nesse caso, o sombreamento é desfeito e o compilador resolve qualquer referência ao mesmo elemento faria se tivesse sido sombreado.</span><span class="sxs-lookup"><span data-stu-id="4675f-140">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="4675f-141">Esse elemento é o elemento acessível com o menor número derivacionais as etapas para trás da classe de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="4675f-141">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="4675f-142">Se o elemento sombreado é um procedimento, a resolução é a versão mais acessível com o mesmo nome, a lista de parâmetros e tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="4675f-142">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="4675f-143">O exemplo a seguir mostra uma hierarquia de herança de três classes.</span><span class="sxs-lookup"><span data-stu-id="4675f-143">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="4675f-144">Cada classe define um `Sub` procedimento `display`, e cada classe derivada sombreia a `display` procedimento em sua classe base.</span><span class="sxs-lookup"><span data-stu-id="4675f-144">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="4675f-145">No exemplo anterior, a classe derivada `secondClass` sombras `display` com um `Private` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4675f-145">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="4675f-146">Ao módulo `callDisplay` chamadas `display` na `secondClass`, o código de chamada está fora `secondClass` e, portanto, não é possível acessar particular `display` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4675f-146">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="4675f-147">O sombreamento é desfeito, e o compilador resolve a referência para a classe base `display` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4675f-147">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="4675f-148">No entanto, a classe derivada adicional `thirdClass` declara `display` como `Public`, portanto o código em `callDisplay` pode acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="4675f-148">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="4675f-149">Sombreamento e sobreposição</span><span class="sxs-lookup"><span data-stu-id="4675f-149">Shadowing and Overriding</span></span>  
 <span data-ttu-id="4675f-150">Não confunda sombreamento com substituição.</span><span class="sxs-lookup"><span data-stu-id="4675f-150">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="4675f-151">Ambos são usados quando uma classe derivada herda de uma classe base e os dois redefinem um elemento declarado com outro.</span><span class="sxs-lookup"><span data-stu-id="4675f-151">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="4675f-152">Mas há diferenças significativas entre os dois.</span><span class="sxs-lookup"><span data-stu-id="4675f-152">But there are significant differences between the two.</span></span> <span data-ttu-id="4675f-153">Para obter uma comparação, consulte [diferenças entre sombreamento e substituindo](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="4675f-153">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="4675f-154">Sombreamento e sobrecarga</span><span class="sxs-lookup"><span data-stu-id="4675f-154">Shadowing and Overloading</span></span>  
 <span data-ttu-id="4675f-155">Se você sombrear o mesmo elemento de classe base com mais de um elemento em sua classe derivada, os elementos de sombreamento se tornarão versões sobrecarregadas desse elemento.</span><span class="sxs-lookup"><span data-stu-id="4675f-155">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="4675f-156">Para obter mais informações, consulte [sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="4675f-156">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="4675f-157">Acessando um elemento sombreado</span><span class="sxs-lookup"><span data-stu-id="4675f-157">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="4675f-158">Quando você acessar um elemento de uma classe derivada, você normalmente o faz até a instância atual da classe derivada, qualificando o nome do elemento com o `Me` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="4675f-158">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="4675f-159">Se sua classe derivada sombreia o elemento na classe base, você pode acessar o elemento de classe base usando o `MyBase` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="4675f-159">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="4675f-160">Para obter um exemplo de como acessar um elemento sombreado, consulte [como: acessar uma variável oculta por uma classe derivada de](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="4675f-160">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="4675f-161">Declaração de variável de objeto</span><span class="sxs-lookup"><span data-stu-id="4675f-161">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="4675f-162">Também pode afetar como você cria a variável de objeto, se a classe derivada acessa um elemento de sombreamento ou o elemento sombreado.</span><span class="sxs-lookup"><span data-stu-id="4675f-162">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="4675f-163">O exemplo a seguir cria dois objetos de uma classe derivada, mas um objeto é declarado como a classe base e o outro como a classe derivada.</span><span class="sxs-lookup"><span data-stu-id="4675f-163">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="4675f-164">No exemplo anterior, a variável `basObj` é declarada como a classe base.</span><span class="sxs-lookup"><span data-stu-id="4675f-164">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="4675f-165">Atribuindo um `dervCls` objeto para ele constitui uma conversão de ampliação e, portanto, é válido.</span><span class="sxs-lookup"><span data-stu-id="4675f-165">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="4675f-166">No entanto, a classe base não pode acessar a versão de sombreamento da variável `z` na classe derivada, então o compilador resolve `basObj.z` para o valor original da classe base.</span><span class="sxs-lookup"><span data-stu-id="4675f-166">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4675f-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4675f-167">See Also</span></span>  
 [<span data-ttu-id="4675f-168">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="4675f-168">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="4675f-169">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4675f-169">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="4675f-170">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="4675f-170">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="4675f-171">Sombras</span><span class="sxs-lookup"><span data-stu-id="4675f-171">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="4675f-172">Substituições</span><span class="sxs-lookup"><span data-stu-id="4675f-172">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="4675f-173">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="4675f-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="4675f-174">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="4675f-174">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
