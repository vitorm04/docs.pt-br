---
title: Criando Interfaces genéricas variante (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: d6afddf018b4608418f82fa851d018f2c3e1d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663252"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="b7f83-102">Criando Interfaces genéricas variante (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7f83-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="b7f83-103">Você pode declarar parâmetros de tipo genérico em interfaces como covariantes ou contravariantes.</span><span class="sxs-lookup"><span data-stu-id="b7f83-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="b7f83-104">A *Covariância* permite que os métodos de interface tenham tipos de retorno mais derivados que aqueles definidos pelos parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="b7f83-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="b7f83-105">A *Contravariância* permite que os métodos de interface tenham tipos de argumentos que são menos derivados que aqueles especificados pelos parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="b7f83-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="b7f83-106">Uma interface genérica que tenha parâmetros de tipo genérico covariantes ou contravariantes é chamada de *variante*.</span><span class="sxs-lookup"><span data-stu-id="b7f83-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7f83-107">O .NET Framework 4 introduziu o suporte à variação para diversas interfaces genéricas existentes.</span><span class="sxs-lookup"><span data-stu-id="b7f83-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="b7f83-108">Para obter a lista das interfaces de variantes no .NET Framework, consulte [variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="b7f83-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="b7f83-109">Declarando interfaces genéricas variantes</span><span class="sxs-lookup"><span data-stu-id="b7f83-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="b7f83-110">Você pode declarar interfaces genéricas variantes usando as palavras-chave `in` e `out` para parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="b7f83-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7f83-111">`ByRef` os parâmetros no Visual Basic não podem ser variantes.</span><span class="sxs-lookup"><span data-stu-id="b7f83-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="b7f83-112">Os tipos de valor também não dão suporte à variância.</span><span class="sxs-lookup"><span data-stu-id="b7f83-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="b7f83-113">Você pode declarar um parâmetro de tipo genérico como covariante usando a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="b7f83-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="b7f83-114">O tipo de covariante deve satisfazer as condições a seguir:</span><span class="sxs-lookup"><span data-stu-id="b7f83-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="b7f83-115">O tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="b7f83-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="b7f83-116">Isso é ilustrado no exemplo a seguir, no qual o tipo `R` é declarado covariante.</span><span class="sxs-lookup"><span data-stu-id="b7f83-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     <span data-ttu-id="b7f83-117">Há uma exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="b7f83-117">There is one exception to this rule.</span></span> <span data-ttu-id="b7f83-118">Se você tiver um delegado genérico contravariante como um parâmetro de método, você poderá usar o tipo como um parâmetro de tipo genérico para o delegado.</span><span class="sxs-lookup"><span data-stu-id="b7f83-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="b7f83-119">Isso é ilustrado pelo tipo `R` no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7f83-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="b7f83-120">Para obter mais informações, consulte [variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [usando variância para delegados Func e Action genérico (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b7f83-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   <span data-ttu-id="b7f83-121">O tipo não é usado como uma restrição genérica para os métodos de interface.</span><span class="sxs-lookup"><span data-stu-id="b7f83-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="b7f83-122">O código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="b7f83-122">This is illustrated in the following code.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 <span data-ttu-id="b7f83-123">Você pode declarar um parâmetro de tipo genérico como contravariante usando a palavra-chave `in`.</span><span class="sxs-lookup"><span data-stu-id="b7f83-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="b7f83-124">O tipo contravariante pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno dos métodos de interface.</span><span class="sxs-lookup"><span data-stu-id="b7f83-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="b7f83-125">O tipo contravariante também pode ser usado para restrições genéricas.</span><span class="sxs-lookup"><span data-stu-id="b7f83-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="b7f83-126">O código a seguir mostra como declarar uma interface contravariante e usar uma restrição genérica para um de seus métodos.</span><span class="sxs-lookup"><span data-stu-id="b7f83-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 <span data-ttu-id="b7f83-127">Também é possível oferecer suporte à covariância e contravariância na mesma interface, mas para parâmetros de tipo diferentes, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7f83-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 <span data-ttu-id="b7f83-128">No Visual Basic, você não pode declarar eventos em interfaces variantes sem especificar o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="b7f83-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="b7f83-129">Além disso, uma interface variante não pode ter aninhados, classes, enumerações ou estruturas, mas ela pode ter interfaces aninhadas.</span><span class="sxs-lookup"><span data-stu-id="b7f83-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="b7f83-130">O código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="b7f83-130">This is illustrated in the following code.</span></span>  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="b7f83-131">Implementando interfaces genéricas variantes</span><span class="sxs-lookup"><span data-stu-id="b7f83-131">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="b7f83-132">Você pode implementar interfaces genéricas variantes em classes, através da mesma sintaxe que é usada para interfaces invariantes.</span><span class="sxs-lookup"><span data-stu-id="b7f83-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="b7f83-133">O exemplo de código a seguir mostra como implementar uma interface covariante em uma classe genérica.</span><span class="sxs-lookup"><span data-stu-id="b7f83-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 <span data-ttu-id="b7f83-134">As classes que implementam interfaces variantes são invariantes.</span><span class="sxs-lookup"><span data-stu-id="b7f83-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="b7f83-135">Por exemplo, considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7f83-135">For example, consider the following code.</span></span>  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="b7f83-136">Estendendo interfaces genéricas variantes</span><span class="sxs-lookup"><span data-stu-id="b7f83-136">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="b7f83-137">Quando você estende uma interface genérica variante, é necessário usar as palavras-chave `in` e `out` para especificar explicitamente se a interface derivada dará suporte à variância.</span><span class="sxs-lookup"><span data-stu-id="b7f83-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="b7f83-138">O compilador não deduz a variância da interface que está sendo estendida.</span><span class="sxs-lookup"><span data-stu-id="b7f83-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="b7f83-139">Por exemplo, considere as seguintes interfaces.</span><span class="sxs-lookup"><span data-stu-id="b7f83-139">For example, consider the following interfaces.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 <span data-ttu-id="b7f83-140">No `Invariant(Of T)` da interface, o parâmetro de tipo genérico `T` é invariável, enquanto que no `IExtCovariant (Of Out T)`o parâmetro de tipo é covariante, embora as duas interfaces estendam a mesma interface.</span><span class="sxs-lookup"><span data-stu-id="b7f83-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="b7f83-141">A mesma regra é aplicada aos parâmetros de tipo genérico contravariantes.</span><span class="sxs-lookup"><span data-stu-id="b7f83-141">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="b7f83-142">Você pode criar uma interface que estende tanto a interface em que o parâmetro de tipo genérico `T` é covariante, quanto a interface em que ele é contravariante, caso na interface de extensão o parâmetro de tipo genérico `T` seja invariante.</span><span class="sxs-lookup"><span data-stu-id="b7f83-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="b7f83-143">Isso é ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7f83-143">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 <span data-ttu-id="b7f83-144">No entanto, se um parâmetro de tipo genérico `T` for declarado covariante em uma interface, você não poderá declará-lo contravariante na interface de extensão ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="b7f83-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="b7f83-145">Isso é ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7f83-145">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="b7f83-146">Evitando ambiguidade</span><span class="sxs-lookup"><span data-stu-id="b7f83-146">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="b7f83-147">Ao implementar interfaces genéricas variantes, a variância, às vezes, pode levar à ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="b7f83-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="b7f83-148">Isso deve ser evitado.</span><span class="sxs-lookup"><span data-stu-id="b7f83-148">This should be avoided.</span></span>  
  
 <span data-ttu-id="b7f83-149">Por exemplo, se você implementar explicitamente a mesma interface genérica variante com parâmetros de tipo genérico diferentes em uma classe, isso poderá criar ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="b7f83-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="b7f83-150">O compilador não produzirá um erro nesse caso, mas não está especificado qual implementação de interface será escolhida em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b7f83-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="b7f83-151">Isso poderá causar bugs sutis no seu código.</span><span class="sxs-lookup"><span data-stu-id="b7f83-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="b7f83-152">Considere o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7f83-152">Consider the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7f83-153">Com `Option Strict Off`, Visual Basic gera um aviso do compilador quando há uma implementação de interface ambíguo.</span><span class="sxs-lookup"><span data-stu-id="b7f83-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="b7f83-154">Com `Option Strict On`, Visual Basic gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="b7f83-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 <span data-ttu-id="b7f83-155">Neste exemplo, não está especificado como o método `pets.GetEnumerator` escolherá entre `Cat` e `Dog`.</span><span class="sxs-lookup"><span data-stu-id="b7f83-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="b7f83-156">Isso poderá causar problemas em seu código.</span><span class="sxs-lookup"><span data-stu-id="b7f83-156">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f83-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7f83-157">See also</span></span>
- [<span data-ttu-id="b7f83-158">Variação em interfaces genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7f83-158">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="b7f83-159">Usando variação para delegados genéricos Func e Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7f83-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
