---
title: Variância em interfaces genéricas (C#)
ms.date: 04/10/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 5874a39a57f85695bedc3d1ffa61adf19fcdbe37
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480775"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="724ec-102">Variância em interfaces genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="724ec-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="724ec-103">O .NET Framework 4 introduziu o suporte à variação para diversas interfaces genéricas existentes.</span><span class="sxs-lookup"><span data-stu-id="724ec-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="724ec-104">O suporte à variação possibilita a conversão implícita de classes que implementam essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="724ec-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="724ec-105">A partir do .NET Framework 4, as seguintes interfaces são variantes:</span><span class="sxs-lookup"><span data-stu-id="724ec-105">Staring with .NET Framework 4, the following interfaces are variant:</span></span>

- <xref:System.Collections.Generic.IEnumerable%601> <span data-ttu-id="724ec-106">(T é covariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-106">(T is covariant)</span></span>

- <xref:System.Collections.Generic.IEnumerator%601> <span data-ttu-id="724ec-107">(T é covariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-107">(T is covariant)</span></span>

- <xref:System.Linq.IQueryable%601> <span data-ttu-id="724ec-108">(T é covariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-108">(T is covariant)</span></span>

- <xref:System.Linq.IGrouping%602> <span data-ttu-id="724ec-109">(`TKey` e `TElement` são covariantes)</span><span class="sxs-lookup"><span data-stu-id="724ec-109">(`TKey` and `TElement` are covariant)</span></span>

- <xref:System.Collections.Generic.IComparer%601> <span data-ttu-id="724ec-110">(T é contravariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-110">(T is contravariant)</span></span>

- <xref:System.Collections.Generic.IEqualityComparer%601> <span data-ttu-id="724ec-111">(T é contravariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-111">(T is contravariant)</span></span>

- <xref:System.IComparable%601> <span data-ttu-id="724ec-112">(T é contravariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-112">(T is contravariant)</span></span>

<span data-ttu-id="724ec-113">A partir do .NET Framework 4.5, as seguintes interfaces são variantes:</span><span class="sxs-lookup"><span data-stu-id="724ec-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <xref:System.Collections.Generic.IReadOnlyList%601> <span data-ttu-id="724ec-114">(T é contravariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-114">(T is contravariant)</span></span>

- <xref:System.Collections.Generic.IReadOnlyCollection%601> <span data-ttu-id="724ec-115">(T é contravariante)</span><span class="sxs-lookup"><span data-stu-id="724ec-115">(T is contravariant)</span></span>

<span data-ttu-id="724ec-116">A covariância permite que um método tenha um tipo de retorno mais derivados que aquele definidos pelo parâmetro de tipo genérico da interface.</span><span class="sxs-lookup"><span data-stu-id="724ec-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="724ec-117">Para ilustrar o recurso de covariância, considere estas interfaces genéricas: `IEnumerable<Object>` e `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="724ec-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="724ec-118">A interface `IEnumerable<String>` não herda a interface `IEnumerable<Object>`.</span><span class="sxs-lookup"><span data-stu-id="724ec-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="724ec-119">No entanto, o tipo `String` herda o tipo `Object` e, em alguns casos, talvez você queira atribuir objetos dessas interfaces uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="724ec-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="724ec-120">Isso será mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="724ec-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="724ec-121">Em versões anteriores do .NET Framework, esse código causa um erro de compilação em C# e, se `Option Strict` estiver ativado, no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="724ec-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="724ec-122">Mas agora você pode usar `strings` em vez de `objects`, conforme mostrado no exemplo anterior, porque a interface <xref:System.Collections.Generic.IEnumerable%601> é covariante.</span><span class="sxs-lookup"><span data-stu-id="724ec-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="724ec-123">A contravariância permite que um método tenha tipos de argumentos menos derivados que aquele especificado pelo parâmetro genérico da interface.</span><span class="sxs-lookup"><span data-stu-id="724ec-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="724ec-124">Para ilustrar a contravariância, suponha que você tenha criado uma classe `BaseComparer` para comparar instâncias da classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="724ec-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="724ec-125">A classe `BaseComparer` implementa a interface `IEqualityComparer<BaseClass>`.</span><span class="sxs-lookup"><span data-stu-id="724ec-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="724ec-126">Como a interface <xref:System.Collections.Generic.IEqualityComparer%601> agora é contravariante, você pode usar `BaseComparer` para comparar instâncias de classes que herdam a classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="724ec-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="724ec-127">Isso será mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="724ec-127">This is shown in the following code example.</span></span>

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

<span data-ttu-id="724ec-128">Para ver mais exemplos, consulte [Usando variação em interfaces para coleções genéricas (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="724ec-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="724ec-129">A variação em interfaces genéricas tem suporte somente para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="724ec-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="724ec-130">Tipos de valor não dão suporte à variação.</span><span class="sxs-lookup"><span data-stu-id="724ec-130">Value types do not support variance.</span></span> <span data-ttu-id="724ec-131">Por exemplo, `IEnumerable<int>` não pode ser convertido implicitamente em `IEnumerable<object>`, porque inteiros são representados por um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="724ec-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="724ec-132">Também é importante lembrar que as classes que implementam interfaces variantes ainda são invariantes.</span><span class="sxs-lookup"><span data-stu-id="724ec-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="724ec-133">Por exemplo, embora <xref:System.Collections.Generic.List%601> implemente a interface covariante <xref:System.Collections.Generic.IEnumerable%601>, você não pode converter implicitamente `List<Object>` para `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="724ec-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="724ec-134">Isso é ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="724ec-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="724ec-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="724ec-135">See also</span></span>

- [<span data-ttu-id="724ec-136">Usando variação em interfaces para Coleções Genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="724ec-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="724ec-137">Criando interfaces genéricas variantes (C#)</span><span class="sxs-lookup"><span data-stu-id="724ec-137">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="724ec-138">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="724ec-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="724ec-139">Variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="724ec-139">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
