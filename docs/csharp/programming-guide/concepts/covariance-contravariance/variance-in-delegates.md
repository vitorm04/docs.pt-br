---
title: Variação em delegados (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 3dabac4e532198871cf05d639aa692751ab17ae1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577471"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="2d727-102">Variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="2d727-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="2d727-103">O .NET Framework 3.5 introduziu o suporte a variação para assinaturas de método correspondentes com tipos de delegados em todos os delegados do C#.</span><span class="sxs-lookup"><span data-stu-id="2d727-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="2d727-104">Isso significa que você pode atribuir a delegados não apenas os métodos que têm assinaturas correspondentes, mas também métodos que retornam tipos mais derivados (covariância) ou que aceitam parâmetros que têm tipos menos derivados (contravariância) do que o especificado pelo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="2d727-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="2d727-105">Isso inclui delegados genéricos e não genéricos.</span><span class="sxs-lookup"><span data-stu-id="2d727-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="2d727-106">Por exemplo, considere o código a seguir, que tem duas classes e dois delegados: genérico e não genérico.</span><span class="sxs-lookup"><span data-stu-id="2d727-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="2d727-107">Quando cria delegados dos tipos `SampleDelegate` ou `SampleGenericDelegate<A, R>`, você pode atribuir qualquer um dos seguintes métodos a esses delegados.</span><span class="sxs-lookup"><span data-stu-id="2d727-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second first)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived   
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 <span data-ttu-id="2d727-108">O exemplo de código a seguir ilustra a conversão implícita entre a assinatura do método e o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="2d727-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```csharp  
// Assigning a method with a matching signature   
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 <span data-ttu-id="2d727-109">Para obter mais informações, consulte [Usando variação em delegados (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) e [Usando variação para os delegados genéricos Func e Action (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="2d727-109">For more examples, see [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="2d727-110">Variação em parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="2d727-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="2d727-111">No .NET Framework 4 ou posterior, agora você pode habilitar a conversão implícita entre delegados, de modo que delegados genéricos que têm tipos diferentes especificados por parâmetros de tipo genérico podem ser atribuídos uns aos outros, se os tipos forem herdados uns dos outros como é obrigatório de acordo com a variação.</span><span class="sxs-lookup"><span data-stu-id="2d727-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="2d727-112">Para habilitar a conversão implícita, você precisa declarar explicitamente os parâmetros genéricos em um delegado como covariante ou contravariante usando a palavra-chave `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="2d727-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="2d727-113">O exemplo de código a seguir mostra como você pode criar um delegado que tem um parâmetro de tipo genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="2d727-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;             
}  
```  
  
 <span data-ttu-id="2d727-114">Se você usar somente o suporte à para fazer a correspondência de assinaturas de método com tipos de delegados e não usar as palavras-chave `in` e `out`, você poderá perceber que, às vezes, é possível instanciar delegados com métodos ou expressões lambda idênticas, mas não é possível atribuir um delegado a outro.</span><span class="sxs-lookup"><span data-stu-id="2d727-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="2d727-115">No exemplo de código a seguir, `SampleGenericDelegate<String>` não pode ser convertido explicitamente em `SampleGenericDelegate<Object>`, embora `String` herde `Object`.</span><span class="sxs-lookup"><span data-stu-id="2d727-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="2d727-116">Você pode corrigir esse problema marcando o parâmetro genérico `T` com a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="2d727-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for   
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="2d727-117">Delegados genéricos que têm parâmetros de tipo variante no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2d727-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="2d727-118">O .NET Framework 4 introduziu o suporte à variação para parâmetros de tipo genérico em diversos delegados genéricos existentes:</span><span class="sxs-lookup"><span data-stu-id="2d727-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="2d727-119">`Action` delega do namespace <xref:System>, por exemplo, <xref:System.Action%601> e <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="2d727-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="2d727-120">`Func` delega do namespace <xref:System>, por exemplo, <xref:System.Func%601> e <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="2d727-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="2d727-121">O delegado <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="2d727-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="2d727-122">O delegado <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="2d727-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="2d727-123">O delegado <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="2d727-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="2d727-124">Para obter mais informações e exemplos, consulte [Usando variação para delegados genéricos Func e Action (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="2d727-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="2d727-125">Declarando parâmetros de tipo variante em delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="2d727-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="2d727-126">Se um delegado genérico tiver parâmetros de tipo genérico covariantes ou contravariantes, ele poderá ser considerado um *delegado genérico variante*.</span><span class="sxs-lookup"><span data-stu-id="2d727-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="2d727-127">Você pode declarar um parâmetro de tipo genérico covariante em um delegado genérico usando a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="2d727-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="2d727-128">O tipo covariante pode ser usado apenas como um tipo de retorno de método e não como um tipo de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="2d727-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="2d727-129">O exemplo de código a seguir mostra como declarar um delegado genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="2d727-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="2d727-130">Você pode declarar um parâmetro de tipo genérico contravariante em um delegado genérico usando a palavra-chave `in`.</span><span class="sxs-lookup"><span data-stu-id="2d727-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="2d727-131">O tipo contravariante pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno de método.</span><span class="sxs-lookup"><span data-stu-id="2d727-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="2d727-132">O exemplo de código a seguir mostra como declarar um delegado genérico contravariante.</span><span class="sxs-lookup"><span data-stu-id="2d727-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d727-133">Os parâmetros `ref`, `in` e `out` em C# não podem ser marcados como variantes.</span><span class="sxs-lookup"><span data-stu-id="2d727-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="2d727-134">Também é possível dar suporte à variância e à covariância no mesmo delegado, mas para parâmetros de tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="2d727-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="2d727-135">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d727-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="2d727-136">Instanciando e invocando delegados genéricos variantes</span><span class="sxs-lookup"><span data-stu-id="2d727-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="2d727-137">Você pode instanciar e invocar delegados variantes da mesma forma como instancia e invoca delegados invariantes.</span><span class="sxs-lookup"><span data-stu-id="2d727-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="2d727-138">No exemplo a seguir, um delegado é instanciado por uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="2d727-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="2d727-139">Combinando delegados genéricos variantes</span><span class="sxs-lookup"><span data-stu-id="2d727-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="2d727-140">Você não deve combinar delegados variantes.</span><span class="sxs-lookup"><span data-stu-id="2d727-140">You should not combine variant delegates.</span></span> <span data-ttu-id="2d727-141">O método <xref:System.Delegate.Combine%2A> não dá suporte à conversão de delegados variantes e espera que os delegados sejam exatamente do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="2d727-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="2d727-142">Isso pode levar a uma exceção de tempo de execução quando você combina delegados usando o método <xref:System.Delegate.Combine%2A> ou o operador `+`, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d727-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="2d727-143">Variação em parâmetros de tipo genérico para tipos de referência e valor</span><span class="sxs-lookup"><span data-stu-id="2d727-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="2d727-144">A variação para parâmetros de tipo genérico tem suporte apenas para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="2d727-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="2d727-145">Por exemplo, `DVariant<int>` não pode ser convertido implicitamente em `DVariant<Object>` ou `DVariant<long>`, pois inteiro é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2d727-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="2d727-146">O exemplo a seguir demonstra que a variação em parâmetros de tipo genérico não tem suporte para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="2d727-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;              
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d727-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d727-147">See Also</span></span>

- [<span data-ttu-id="2d727-148">Genéricos</span><span class="sxs-lookup"><span data-stu-id="2d727-148">Generics</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="2d727-149">Usando variação para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="2d727-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
- [<span data-ttu-id="2d727-150">Como combinar delegados (delegados multicast)</span><span class="sxs-lookup"><span data-stu-id="2d727-150">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
