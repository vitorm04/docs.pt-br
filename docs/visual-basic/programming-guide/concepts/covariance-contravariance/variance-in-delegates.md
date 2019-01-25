---
title: Variação em delegados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 350f8d6b317f6a82d5b5a718a3d49a4b9ee3e4b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631536"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="c2f4a-102">Variação em delegados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2f4a-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="c2f4a-103">.NET framework 3.5 introduziu suporte à variação para assinaturas de método correspondentes com tipos de delegados em todos os delegados do C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="c2f4a-104">Isso significa que você pode atribuir a delegados não apenas os métodos que têm assinaturas correspondentes, mas também métodos que retornam tipos mais derivados (covariância) ou que aceitam parâmetros que têm tipos menos derivados (contravariância) do que o especificado pelo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="c2f4a-105">Isso inclui delegados genéricos e não genéricos.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="c2f4a-106">Por exemplo, considere o código a seguir, que tem duas classes e dois delegados: genérico e não genérico.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="c2f4a-107">Quando cria delegados dos tipos `SampleDelegate` ou `SampleDelegate(Of A, R)`, você pode atribuir qualquer um dos seguintes métodos a esses delegados.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```vb  
' Matching signature.  
Public Shared Function ASecondRFirst(  
    ByVal second As Second) As First  
    Return New First()  
End Function  
  
' The return type is more derived.  
Public Shared Function ASecondRSecond(  
    ByVal second As Second) As Second  
    Return New Second()  
End Function  
  
' The argument type is less derived.  
Public Shared Function AFirstRFirst(  
    ByVal first As First) As First  
    Return New First()  
End Function  
  
' The return type is more derived   
' and the argument type is less derived.  
Public Shared Function AFirstRSecond(  
    ByVal first As First) As Second  
    Return New Second()  
End Function  
```  
  
 <span data-ttu-id="c2f4a-108">O exemplo de código a seguir ilustra a conversão implícita entre a assinatura do método e o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```vb  
' Assigning a method with a matching signature   
' to a non-generic delegate. No conversion is necessary.  
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a non-generic delegate.  
' The implicit conversion is used.  
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond  
  
' Assigning a method with a matching signature to a generic delegate.  
' No conversion is necessary.  
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a generic delegate.  
' The implicit conversion is used.  
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond  
```  
  
 <span data-ttu-id="c2f4a-109">Para obter mais exemplos, consulte [usando variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) e [usando variância para delegados Func e Action genérico (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c2f4a-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="c2f4a-110">Variação em parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="c2f4a-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="c2f4a-111">No .NET Framework 4 e mais tarde você pode habilitar a conversão implícita entre delegados, para que os delegados genéricos que têm tipos diferentes especificados por parâmetros de tipo genérico podem ser atribuídos uns aos outros, se os tipos forem herdados uns dos outros, conforme exigido pelo variação.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="c2f4a-112">Para habilitar a conversão implícita, você precisa declarar explicitamente os parâmetros genéricos em um delegado como covariante ou contravariante usando a palavra-chave `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="c2f4a-113">O exemplo de código a seguir mostra como você pode criar um delegado que tem um parâmetro de tipo genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```vb  
' Type T is declared covariant by using the out keyword.  
Public Delegate Function SampleGenericDelegate(Of Out T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
    ' You can assign delegates to each other,  
    ' because the type T is declared covariant.  
    Dim dObject As SampleGenericDelegate(Of Object) = dString  
End Sub  
```  
  
 <span data-ttu-id="c2f4a-114">Se você usar somente o suporte à para fazer a correspondência de assinaturas de método com tipos de delegados e não usar as palavras-chave `in` e `out`, você poderá perceber que, às vezes, é possível instanciar delegados com métodos ou expressões lambda idênticas, mas não é possível atribuir um delegado a outro.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="c2f4a-115">No exemplo de código a seguir `SampleGenericDelegate(Of String)` não pode ser explicitamente convertido `SampleGenericDelegate(Of Object)`, embora `String` herda `Object`.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="c2f4a-116">Você pode corrigir esse problema marcando o parâmetro genérico `T` com a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```vb  
Public Delegate Function SampleGenericDelegate(Of T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
  
    ' You can assign the dObject delegate  
    ' to the same lambda expression as dString delegate  
    ' because of the variance support for   
    ' matching method signatures with delegate types.  
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "  
  
    ' The following statement generates a compiler error  
    ' because the generic type T is not marked as covariant.  
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString  
  
End Sub  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="c2f4a-117">Delegados genéricos que têm parâmetros de tipo variante no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c2f4a-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="c2f4a-118">O .NET Framework 4 introduziu o suporte à variação para parâmetros de tipo genérico em diversos delegados genéricos existentes:</span><span class="sxs-lookup"><span data-stu-id="c2f4a-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="c2f4a-119">`Action` delega do namespace <xref:System>, por exemplo, <xref:System.Action%601> e <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="c2f4a-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="c2f4a-120">`Func` delega do namespace <xref:System>, por exemplo, <xref:System.Func%601> e <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="c2f4a-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="c2f4a-121">O delegado <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="c2f4a-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="c2f4a-122">O delegado <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="c2f4a-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="c2f4a-123">O delegado <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="c2f4a-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="c2f4a-124">Para obter mais informações e exemplos, consulte [usando variância para delegados Func e Action genérico (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c2f4a-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="c2f4a-125">Declarando parâmetros de tipo variante em delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="c2f4a-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="c2f4a-126">Se um delegado genérico tiver parâmetros de tipo genérico covariantes ou contravariantes, ele poderá ser considerado um *delegado genérico variante*.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="c2f4a-127">Você pode declarar um parâmetro de tipo genérico covariante em um delegado genérico usando a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="c2f4a-128">O tipo covariante pode ser usado apenas como um tipo de retorno de método e não como um tipo de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="c2f4a-129">O exemplo de código a seguir mostra como declarar um delegado genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 <span data-ttu-id="c2f4a-130">Você pode declarar um parâmetro de tipo genérico contravariante em um delegado genérico usando a palavra-chave `in`.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="c2f4a-131">O tipo contravariante pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno de método.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="c2f4a-132">O exemplo de código a seguir mostra como declarar um delegado genérico contravariante.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2f4a-133">`ByRef` os parâmetros no Visual Basic não podem ser marcados como variantes.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="c2f4a-134">Também é possível dar suporte à variância e à covariância no mesmo delegado, mas para parâmetros de tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="c2f4a-135">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-135">This is shown in the following example.</span></span>  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="c2f4a-136">Instanciando e invocando delegados genéricos variantes</span><span class="sxs-lookup"><span data-stu-id="c2f4a-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="c2f4a-137">Você pode instanciar e invocar delegados variantes da mesma forma como instancia e invoca delegados invariantes.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="c2f4a-138">No exemplo a seguir, um delegado é instanciado por uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="c2f4a-139">Combinando delegados genéricos variantes</span><span class="sxs-lookup"><span data-stu-id="c2f4a-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="c2f4a-140">Você não deve combinar delegados variantes.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-140">You should not combine variant delegates.</span></span> <span data-ttu-id="c2f4a-141">O método <xref:System.Delegate.Combine%2A> não dá suporte à conversão de delegados variantes e espera que os delegados sejam exatamente do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="c2f4a-142">Isso pode levar a uma exceção de tempo de execução quando você combina delegados usando o <xref:System.Delegate.Combine%2A> método (no C# e Visual Basic) ou usando o `+` operador (em C#), conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="c2f4a-143">Variação em parâmetros de tipo genérico para tipos de referência e valor</span><span class="sxs-lookup"><span data-stu-id="c2f4a-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="c2f4a-144">A variação para parâmetros de tipo genérico tem suporte apenas para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="c2f4a-145">Por exemplo, `DVariant(Of Int)`não pode ser convertido implicitamente em `DVariant(Of Object)` ou `DVariant(Of Long)`, pois inteiro é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="c2f4a-146">O exemplo a seguir demonstra que a variação em parâmetros de tipo genérico não tem suporte para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="c2f4a-147">Conversão de delegado reduzida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2f4a-147">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="c2f4a-148">Conversão de delegado reduzida permite mais flexibilidade na correspondência de assinaturas de método com tipos de delegados.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="c2f4a-149">Por exemplo, ele permite omitir especificações de parâmetro e omitir os valores de retorno de função, quando você atribui um método a um delegado.</span><span class="sxs-lookup"><span data-stu-id="c2f4a-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="c2f4a-150">Para obter mais informações, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="c2f4a-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f4a-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2f4a-151">See also</span></span>
- [<span data-ttu-id="c2f4a-152">Genéricos</span><span class="sxs-lookup"><span data-stu-id="c2f4a-152">Generics</span></span>](~/docs/standard/generics/index.md)
- [<span data-ttu-id="c2f4a-153">Usando variação para delegados genéricos Func e Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2f4a-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
