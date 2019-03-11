---
title: Criando interfaces genéricas variantes (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: ad82ba27a98d27a18d9cff1e65ab929cd9d711a6
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673750"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="5676e-102">Criando interfaces genéricas variantes (C#)</span><span class="sxs-lookup"><span data-stu-id="5676e-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="5676e-103">Você pode declarar parâmetros de tipo genérico em interfaces como covariantes ou contravariantes.</span><span class="sxs-lookup"><span data-stu-id="5676e-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="5676e-104">A *Covariância* permite que os métodos de interface tenham tipos de retorno mais derivados que aqueles definidos pelos parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="5676e-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="5676e-105">A *Contravariância* permite que os métodos de interface tenham tipos de argumentos que são menos derivados que aqueles especificados pelos parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="5676e-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="5676e-106">Uma interface genérica que tenha parâmetros de tipo genérico covariantes ou contravariantes é chamada de *variante*.</span><span class="sxs-lookup"><span data-stu-id="5676e-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="5676e-107">O .NET Framework 4 introduziu o suporte à variação para diversas interfaces genéricas existentes.</span><span class="sxs-lookup"><span data-stu-id="5676e-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="5676e-108">Para obter a lista das interfaces de variantes no .NET Framework, consulte [Variância em interfaces genéricas (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="5676e-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="5676e-109">Declarando interfaces genéricas variantes</span><span class="sxs-lookup"><span data-stu-id="5676e-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="5676e-110">Você pode declarar interfaces genéricas variantes usando as palavras-chave `in` e `out` para parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="5676e-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5676e-111">Os parâmetros `ref`, `in` e `out` no C# não podem ser variantes.</span><span class="sxs-lookup"><span data-stu-id="5676e-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="5676e-112">Os tipos de valor também não dão suporte à variância.</span><span class="sxs-lookup"><span data-stu-id="5676e-112">Value types also do not support variance.</span></span>

<span data-ttu-id="5676e-113">Você pode declarar um parâmetro de tipo genérico como covariante usando a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="5676e-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="5676e-114">O tipo de covariante deve satisfazer as condições a seguir:</span><span class="sxs-lookup"><span data-stu-id="5676e-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="5676e-115">O tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="5676e-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="5676e-116">Isso é ilustrado no exemplo a seguir, no qual o tipo `R` é declarado covariante.</span><span class="sxs-lookup"><span data-stu-id="5676e-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="5676e-117">Há uma exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="5676e-117">There is one exception to this rule.</span></span> <span data-ttu-id="5676e-118">Se você tiver um delegado genérico contravariante como um parâmetro de método, você poderá usar o tipo como um parâmetro de tipo genérico para o delegado.</span><span class="sxs-lookup"><span data-stu-id="5676e-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="5676e-119">Isso é ilustrado pelo tipo `R` no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5676e-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="5676e-120">Para obter mais informações, consulte [Variância em delegados (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [Usando variância para delegados genéricos Func e Action (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="5676e-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="5676e-121">O tipo não é usado como uma restrição genérica para os métodos de interface.</span><span class="sxs-lookup"><span data-stu-id="5676e-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="5676e-122">O código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="5676e-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="5676e-123">Você pode declarar um parâmetro de tipo genérico como contravariante usando a palavra-chave `in`.</span><span class="sxs-lookup"><span data-stu-id="5676e-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="5676e-124">O tipo contravariante pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno dos métodos de interface.</span><span class="sxs-lookup"><span data-stu-id="5676e-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="5676e-125">O tipo contravariante também pode ser usado para restrições genéricas.</span><span class="sxs-lookup"><span data-stu-id="5676e-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="5676e-126">O código a seguir mostra como declarar uma interface contravariante e usar uma restrição genérica para um de seus métodos.</span><span class="sxs-lookup"><span data-stu-id="5676e-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="5676e-127">Também é possível oferecer suporte à covariância e contravariância na mesma interface, mas para parâmetros de tipo diferentes, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5676e-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="5676e-128">Implementando interfaces genéricas variantes</span><span class="sxs-lookup"><span data-stu-id="5676e-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="5676e-129">Você pode implementar interfaces genéricas variantes em classes, através da mesma sintaxe que é usada para interfaces invariantes.</span><span class="sxs-lookup"><span data-stu-id="5676e-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="5676e-130">O exemplo de código a seguir mostra como implementar uma interface covariante em uma classe genérica.</span><span class="sxs-lookup"><span data-stu-id="5676e-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```csharp
interface ICovariant<out R>
{
    R GetSomething();
}
class SampleImplementation<R> : ICovariant<R>
{
    public R GetSomething()
    {
        // Some code.
        return default(R);
    }
}
```

<span data-ttu-id="5676e-131">As classes que implementam interfaces variantes são invariantes.</span><span class="sxs-lookup"><span data-stu-id="5676e-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="5676e-132">Por exemplo, considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5676e-132">For example, consider the following code.</span></span>

```csharp
// The interface is covariant.
ICovariant<Button> ibutton = new SampleImplementation<Button>();
ICovariant<Object> iobj = ibutton;

// The class is invariant.
SampleImplementation<Button> button = new SampleImplementation<Button>();
// The following statement generates a compiler error
// because classes are invariant.
// SampleImplementation<Object> obj = button;
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="5676e-133">Estendendo interfaces genéricas variantes</span><span class="sxs-lookup"><span data-stu-id="5676e-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="5676e-134">Quando você estende uma interface genérica variante, é necessário usar as palavras-chave `in` e `out` para especificar explicitamente se a interface derivada dará suporte à variância.</span><span class="sxs-lookup"><span data-stu-id="5676e-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="5676e-135">O compilador não deduz a variância da interface que está sendo estendida.</span><span class="sxs-lookup"><span data-stu-id="5676e-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="5676e-136">Por exemplo, considere as seguintes interfaces.</span><span class="sxs-lookup"><span data-stu-id="5676e-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="5676e-137">Na interface `IInvariant<T>`, o parâmetro de tipo genérico `T` é invariante, enquanto que no `IExtCovariant<out T>` o parâmetro de tipo é covariante, embora as duas interfaces estendam a mesma interface.</span><span class="sxs-lookup"><span data-stu-id="5676e-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="5676e-138">A mesma regra é aplicada aos parâmetros de tipo genérico contravariantes.</span><span class="sxs-lookup"><span data-stu-id="5676e-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="5676e-139">Você pode criar uma interface que estende tanto a interface em que o parâmetro de tipo genérico `T` é covariante, quanto a interface em que ele é contravariante, caso na interface de extensão o parâmetro de tipo genérico `T` seja invariante.</span><span class="sxs-lookup"><span data-stu-id="5676e-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="5676e-140">Isso é ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5676e-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="5676e-141">No entanto, se um parâmetro de tipo genérico `T` for declarado covariante em uma interface, você não poderá declará-lo contravariante na interface de extensão ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="5676e-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="5676e-142">Isso é ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5676e-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="5676e-143">Evitando ambiguidade</span><span class="sxs-lookup"><span data-stu-id="5676e-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="5676e-144">Ao implementar interfaces genéricas variantes, a variância, às vezes, pode levar à ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="5676e-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="5676e-145">Isso deve ser evitado.</span><span class="sxs-lookup"><span data-stu-id="5676e-145">This should be avoided.</span></span>

<span data-ttu-id="5676e-146">Por exemplo, se você implementar explicitamente a mesma interface genérica variante com parâmetros de tipo genérico diferentes em uma classe, isso poderá criar ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="5676e-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="5676e-147">O compilador não produzirá um erro nesse caso, mas não está especificado qual implementação de interface será escolhida em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5676e-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="5676e-148">Isso poderá causar bugs sutis no seu código.</span><span class="sxs-lookup"><span data-stu-id="5676e-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="5676e-149">Considere o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5676e-149">Consider the following code example.</span></span>

```csharp
// Simple class hierarchy.
class Animal { }
class Cat : Animal { }
class Dog : Animal { }

// This class introduces ambiguity
// because IEnumerable<out T> is covariant.
class Pets : IEnumerable<Cat>, IEnumerable<Dog>
{
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()
    {
        Console.WriteLine("Cat");
        // Some code.
        return null;
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        // Some code.
        return null;
    }

    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()
    {
        Console.WriteLine("Dog");
        // Some code.
        return null;
    }
}
class Program
{
    public static void Test()
    {
        IEnumerable<Animal> pets = new Pets();
        pets.GetEnumerator();
    }
}
```

<span data-ttu-id="5676e-150">Neste exemplo, não está especificado como o método `pets.GetEnumerator` escolherá entre `Cat` e `Dog`.</span><span class="sxs-lookup"><span data-stu-id="5676e-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="5676e-151">Isso poderá causar problemas em seu código.</span><span class="sxs-lookup"><span data-stu-id="5676e-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="5676e-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5676e-152">See also</span></span>

- [<span data-ttu-id="5676e-153">Variância em interfaces genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="5676e-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="5676e-154">Usando variação para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="5676e-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
