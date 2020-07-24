---
title: Como adicionar métodos personalizados para consultas LINQ (C#)
description: Saiba como estender o conjunto de métodos que você pode usar para consultas LINQ adicionando métodos de extensão à <T> interface IEnumerable em C#.
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: fac0eb4e14eb3bb36313232a7d7fa3060c0ac171
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103603"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="b85e8-103">Como adicionar métodos personalizados para consultas LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="b85e8-103">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="b85e8-104">Você pode estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando os métodos de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b85e8-104">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="b85e8-105">Por exemplo, além do padrão médio ou máximo de operações, você pode criar um método de agregação personalizado para calcular um único valor de uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="b85e8-105">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="b85e8-106">Você também pode criar um método que funciona como um filtro personalizado ou como uma transformação de dados específicos para uma sequência de valores e que retorna uma nova sequência.</span><span class="sxs-lookup"><span data-stu-id="b85e8-106">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="b85e8-107">Exemplos desses métodos são <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A> e <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="b85e8-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="b85e8-108">Ao estender a interface <xref:System.Collections.Generic.IEnumerable%601>, você pode aplicar seus métodos personalizados para qualquer coleção enumerável.</span><span class="sxs-lookup"><span data-stu-id="b85e8-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="b85e8-109">Para obter mais informações, consulte [Métodos de extensão](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b85e8-109">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="b85e8-110">Adicionando um método de agregação</span><span class="sxs-lookup"><span data-stu-id="b85e8-110">Adding an Aggregate Method</span></span>

<span data-ttu-id="b85e8-111">Um método de agregação calcula um valor único de um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="b85e8-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="b85e8-112">O LINQ fornece vários métodos de agregação, incluindo <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A> e <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="b85e8-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="b85e8-113">Você pode criar seu próprio método de agregação, adicionando um método de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b85e8-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="b85e8-114">O exemplo de código a seguir mostra como criar um método de extensão chamado `Median` para calcular uma mediana de uma sequência de números do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="b85e8-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        var countOfElementsInTheSet = source?.Count() ?? 0;

        if (countOfElementsInTheSet == 0)
        {
            throw new InvalidOperationException("Cannot compute median for a null or empty set.");
        }

        var sortedList = (from number in source
                         orderby number
                         select number).ToList();

        int itemIndex = countOfElementsInTheSet / 2;

        if (countOfElementsInTheSet % 2 == 0)
        {
            // Even number of items.
            return (sortedList[itemIndex] + sortedList[itemIndex - 1]) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList[itemIndex];
        }
    }
}
```

<span data-ttu-id="b85e8-115">Você chama esse método de extensão para qualquer coleção enumerável da mesma maneira que chama outros métodos de agregação da interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b85e8-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="b85e8-116">O exemplo de código a seguir mostra como usar o método `Median` para uma matriz do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="b85e8-116">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="b85e8-117">Sobrecarregando um método de agregação para aceitar vários tipos</span><span class="sxs-lookup"><span data-stu-id="b85e8-117">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="b85e8-118">Você pode sobrecarregar o método de agregação para que ele aceite sequências de vários tipos.</span><span class="sxs-lookup"><span data-stu-id="b85e8-118">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="b85e8-119">A abordagem padrão é criar uma sobrecarga para cada tipo.</span><span class="sxs-lookup"><span data-stu-id="b85e8-119">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="b85e8-120">Outra abordagem é criar uma sobrecarga que vai pegar um tipo genérico e convertê-lo em um tipo específico, usando um delegado.</span><span class="sxs-lookup"><span data-stu-id="b85e8-120">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="b85e8-121">Você também pode combinar as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="b85e8-121">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="b85e8-122">Para criar uma sobrecarga para cada tipo</span><span class="sxs-lookup"><span data-stu-id="b85e8-122">To create an overload for each type</span></span>

<span data-ttu-id="b85e8-123">Você pode criar uma sobrecarga específica para cada tipo que deseja oferecer suporte.</span><span class="sxs-lookup"><span data-stu-id="b85e8-123">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="b85e8-124">O exemplo de código a seguir mostra uma sobrecarga do método `Median` para o tipo `integer`.</span><span class="sxs-lookup"><span data-stu-id="b85e8-124">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="b85e8-125">Agora você pode chamar as sobrecargas `Median` para os tipos `integer` e `double`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b85e8-125">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="b85e8-126">Para criar uma sobrecarga genérica</span><span class="sxs-lookup"><span data-stu-id="b85e8-126">To create a generic overload</span></span>

<span data-ttu-id="b85e8-127">Você também pode criar uma sobrecarga que aceita uma sequência de objetos genéricos.</span><span class="sxs-lookup"><span data-stu-id="b85e8-127">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="b85e8-128">Essa sobrecarga recebe um delegado como parâmetro e usa-o para converter uma sequência de objetos de um tipo genérico em um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="b85e8-128">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="b85e8-129">O código a seguir mostra uma sobrecarga do método `Median` que recebe o delegado <xref:System.Func%602> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b85e8-129">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="b85e8-130">Esse delegado recebe um objeto de tipo genérico T e retorna um objeto do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="b85e8-130">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="b85e8-131">Agora você pode chamar o método `Median` para uma sequência de objetos de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="b85e8-131">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="b85e8-132">Se o tipo não tem sua própria sobrecarga de método, você precisa passar um parâmetro delegado.</span><span class="sxs-lookup"><span data-stu-id="b85e8-132">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="b85e8-133">No C# você pode usar uma expressão lambda para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="b85e8-133">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="b85e8-134">Além disso, no Visual Basic, se você usar a cláusula `Aggregate` ou `Group By` em vez da chamada de método, você pode passar qualquer valor ou expressão que estiver no escopo dessa cláusula.</span><span class="sxs-lookup"><span data-stu-id="b85e8-134">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="b85e8-135">O exemplo de código a seguir mostra como chamar o método `Median` para uma matriz de inteiros e para uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b85e8-135">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="b85e8-136">Será calculada a mediana dos comprimentos das cadeias de caracteres na matriz.</span><span class="sxs-lookup"><span data-stu-id="b85e8-136">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="b85e8-137">O exemplo também mostra como passar o parâmetro delegado <xref:System.Func%602> ao método `Median` para cada caso.</span><span class="sxs-lookup"><span data-stu-id="b85e8-137">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="b85e8-138">Adicionando um método que retorna uma coleção</span><span class="sxs-lookup"><span data-stu-id="b85e8-138">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="b85e8-139">Você pode estender a interface <xref:System.Collections.Generic.IEnumerable%601> com um método de consulta personalizada que retorna uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="b85e8-139">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="b85e8-140">Nesse caso, o método deve retornar uma coleção do tipo <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b85e8-140">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b85e8-141">Esses métodos podem ser usados para aplicar transformações de dados ou filtros a uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="b85e8-141">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="b85e8-142">O exemplo a seguir mostra como criar um método de extensão chamado `AlternateElements` que retorna todos os outros elementos em uma coleção, começando pelo primeiro elemento.</span><span class="sxs-lookup"><span data-stu-id="b85e8-142">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

<span data-ttu-id="b85e8-143">Você pode chamar esse método de extensão para qualquer coleção enumerável exatamente como chamaria outros métodos da interface <xref:System.Collections.Generic.IEnumerable%601>, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b85e8-143">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a><span data-ttu-id="b85e8-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="b85e8-144">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="b85e8-145">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="b85e8-145">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
