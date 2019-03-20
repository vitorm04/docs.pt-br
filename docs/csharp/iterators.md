---
title: Iterators
description: Saiba como usar iteradores C# internos e como criar seus próprios métodos iteradores personalizados.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 37ed45fc563eacf0c6bf412dcfb28dbc6db2bb17
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58126039"
---
# <a name="iterators"></a><span data-ttu-id="7d08c-103">Iterators</span><span class="sxs-lookup"><span data-stu-id="7d08c-103">Iterators</span></span>

<span data-ttu-id="7d08c-104">Quase todos os programas que você escrever terão alguma necessidade de iterar em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="7d08c-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="7d08c-105">Você escreverá um código que examina cada item em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="7d08c-105">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="7d08c-106">Você também criará métodos de iterador que são métodos que produzem um iterador para os elementos dessa classe.</span><span class="sxs-lookup"><span data-stu-id="7d08c-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="7d08c-107">Eles podem ser usados para:</span><span class="sxs-lookup"><span data-stu-id="7d08c-107">These can be used for:</span></span>

+ <span data-ttu-id="7d08c-108">Executar uma ação em cada item em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="7d08c-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="7d08c-109">Enumerar uma coleção personalizada.</span><span class="sxs-lookup"><span data-stu-id="7d08c-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="7d08c-110">Estender [LINQ](linq/index.md) ou outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="7d08c-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="7d08c-111">Criar um pipeline de dados em que os dados fluem com eficiência pelos métodos de iterador.</span><span class="sxs-lookup"><span data-stu-id="7d08c-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="7d08c-112">A linguagem C# fornece recursos para esses dois cenários.</span><span class="sxs-lookup"><span data-stu-id="7d08c-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="7d08c-113">Este artigo fornece uma visão geral desses recursos.</span><span class="sxs-lookup"><span data-stu-id="7d08c-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="7d08c-114">Este tutorial tem várias etapas.</span><span class="sxs-lookup"><span data-stu-id="7d08c-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="7d08c-115">Após cada etapa, você poderá executar o aplicativo e ver o progresso.</span><span class="sxs-lookup"><span data-stu-id="7d08c-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="7d08c-116">Você também pode [exibir ou baixar o exemplo concluído](https://github.com/dotnet/samples/blob/master/csharp/iterators) deste tópico.</span><span class="sxs-lookup"><span data-stu-id="7d08c-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="7d08c-117">Para obter instruções de download, consulte [Exemplos e tutoriais](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="7d08c-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="7d08c-118">iterando com foreach</span><span class="sxs-lookup"><span data-stu-id="7d08c-118">Iterating with foreach</span></span>

<span data-ttu-id="7d08c-119">Enumerar uma coleção é simples: A palavra-chave `foreach` enumera uma coleção, executando a instrução inserida uma vez para cada elemento na coleção:</span><span class="sxs-lookup"><span data-stu-id="7d08c-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="7d08c-120">E isso é tudo.</span><span class="sxs-lookup"><span data-stu-id="7d08c-120">That's all there is to it.</span></span> <span data-ttu-id="7d08c-121">Para iterar em todo o conteúdo de uma coleção, a instrução `foreach` é tudo o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="7d08c-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="7d08c-122">No entanto, a instrução `foreach` não é mágica.</span><span class="sxs-lookup"><span data-stu-id="7d08c-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="7d08c-123">Ele se baseia em duas interfaces genéricas definidas na biblioteca do .NET Core para gerar o código necessário para iterar uma coleção: `IEnumerable<T>` e `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="7d08c-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="7d08c-124">Esse mecanismo é explicado mais detalhadamente abaixo.</span><span class="sxs-lookup"><span data-stu-id="7d08c-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="7d08c-125">Essas duas interfaces também têm contrapartes não genéricas: `IEnumerable` e `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="7d08c-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="7d08c-126">As versões [genéricas](programming-guide/generics/index.md) são preferenciais para o código moderno.</span><span class="sxs-lookup"><span data-stu-id="7d08c-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="7d08c-127">Fontes de enumeração com métodos de iterador</span><span class="sxs-lookup"><span data-stu-id="7d08c-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="7d08c-128">Outro ótimo recurso da linguagem C# permite que você crie métodos que criam uma fonte para uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="7d08c-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="7d08c-129">Eles são chamados de *métodos de iterador*.</span><span class="sxs-lookup"><span data-stu-id="7d08c-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="7d08c-130">Um método de iterador define como gerar os objetos em uma sequência quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="7d08c-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="7d08c-131">Você usa as palavras-chave contextuais `yield return` para definir um método iterador.</span><span class="sxs-lookup"><span data-stu-id="7d08c-131">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="7d08c-132">Você poderia escrever esse método para produzir a sequência de inteiros de 0 a 9:</span><span class="sxs-lookup"><span data-stu-id="7d08c-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

<span data-ttu-id="7d08c-133">O código acima mostra instruções `yield return` distintas para destacar o fato de que você pode usar várias instruções `yield return` discretas em um método iterador.</span><span class="sxs-lookup"><span data-stu-id="7d08c-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="7d08c-134">Você pode (e frequentemente o faz) usar outros constructos de linguagem para simplificar o código de um método iterador.</span><span class="sxs-lookup"><span data-stu-id="7d08c-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="7d08c-135">A definição do método abaixo produz a mesma sequência exata de números:</span><span class="sxs-lookup"><span data-stu-id="7d08c-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="7d08c-136">Você não precisa determinar uma ou a outra.</span><span class="sxs-lookup"><span data-stu-id="7d08c-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="7d08c-137">Você pode ter quantas instruções `yield return` forem necessárias para atender as necessidades do seu método:</span><span class="sxs-lookup"><span data-stu-id="7d08c-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
    
    index = 100;
    while (index++ < 110)
        yield return index;
}
```

<span data-ttu-id="7d08c-138">Essa é a sintaxe básica.</span><span class="sxs-lookup"><span data-stu-id="7d08c-138">That's the basic syntax.</span></span> <span data-ttu-id="7d08c-139">Vamos considerar um exemplo do mundo real em que você escreveria um método iterador.</span><span class="sxs-lookup"><span data-stu-id="7d08c-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="7d08c-140">Imagine que você está em um projeto de IoT e os sensores de dispositivo geram um enorme fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="7d08c-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="7d08c-141">Para ter uma noção dos dados, você pode escrever um método realiza a amostragem a cada N elementos de dados.</span><span class="sxs-lookup"><span data-stu-id="7d08c-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="7d08c-142">Esse pequeno método iterador resolve:</span><span class="sxs-lookup"><span data-stu-id="7d08c-142">This small iterator method does the trick:</span></span>

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

<span data-ttu-id="7d08c-143">Há uma restrição importante em métodos de iterador: você não pode ter uma instrução `return` e uma instrução `yield return` no mesmo método.</span><span class="sxs-lookup"><span data-stu-id="7d08c-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="7d08c-144">O seguinte não compilará:</span><span class="sxs-lookup"><span data-stu-id="7d08c-144">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    // generates a compile time error: 
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;  
}
```

<span data-ttu-id="7d08c-145">Essa restrição normalmente não é um problema.</span><span class="sxs-lookup"><span data-stu-id="7d08c-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="7d08c-146">Você tem a opção de usar `yield return` em todo o método ou separar o método original em vários métodos, alguns usando `return` e alguns usando `yield return`.</span><span class="sxs-lookup"><span data-stu-id="7d08c-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="7d08c-147">Você pode modificar um pouco o último método para usar `yield return` em todos os lugares:</span><span class="sxs-lookup"><span data-stu-id="7d08c-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```
 
<span data-ttu-id="7d08c-148">Às vezes, a resposta certa é dividir um método iterador em dois métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="7d08c-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="7d08c-149">Um que usa `return` e outro que usa `yield return`.</span><span class="sxs-lookup"><span data-stu-id="7d08c-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="7d08c-150">Considere uma situação em que você talvez queira retornar uma coleção vazia ou os primeiros cinco números ímpares, com base em um argumento booliano.</span><span class="sxs-lookup"><span data-stu-id="7d08c-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="7d08c-151">Você poderia escrever isso como esses dois métodos:</span><span class="sxs-lookup"><span data-stu-id="7d08c-151">You could write that as these two methods:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index++ < 10)
        if (index % 2 == 1)
            yield return index;
}
```
 
<span data-ttu-id="7d08c-152">Observe os métodos acima.</span><span class="sxs-lookup"><span data-stu-id="7d08c-152">Look at the methods above.</span></span> <span data-ttu-id="7d08c-153">O primeiro usa a instrução `return` padrão para retornar uma coleção vazia ou o iterador criado pelo segundo método.</span><span class="sxs-lookup"><span data-stu-id="7d08c-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="7d08c-154">O segundo método usa a instrução `yield return` para criar a sequência solicitada.</span><span class="sxs-lookup"><span data-stu-id="7d08c-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="7d08c-155">Aprofundamento em `foreach`</span><span class="sxs-lookup"><span data-stu-id="7d08c-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="7d08c-156">A instrução `foreach` se expande em uma expressão padrão que usa as interfaces `IEnumerable<T>` e `IEnumerator<T>` para iterar em todos os elementos de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="7d08c-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="7d08c-157">Ela também minimiza os erros cometidos pelos desenvolvedores por não gerenciarem os recursos adequadamente.</span><span class="sxs-lookup"><span data-stu-id="7d08c-157">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="7d08c-158">O compilador converte o loop `foreach` mostrado no primeiro exemplo em algo semelhante a esse constructo:</span><span class="sxs-lookup"><span data-stu-id="7d08c-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="7d08c-159">O constructo acima representa o código gerado pelo compilador C# da versão 5 e posterior.</span><span class="sxs-lookup"><span data-stu-id="7d08c-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="7d08c-160">Antes da versão 5, a variável `item` tinha um escopo diferente:</span><span class="sxs-lookup"><span data-stu-id="7d08c-160">Prior to version 5, the `item` variable had a different scope:</span></span>

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="7d08c-161">Isso foi alterado porque o comportamento anterior poderia levar a bugs sutis e difíceis de diagnosticar envolvendo expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="7d08c-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="7d08c-162">Para saber mais sobre expressões lambda, confira o artigo sobre [expressões lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7d08c-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="7d08c-163">O código exato gerado pelo compilador é um pouco mais complicada e lida com situações em que o objeto retornado por `GetEnumerator()` implementa a interface `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="7d08c-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="7d08c-164">A expansão completa gera um código mais semelhante a esse:</span><span class="sxs-lookup"><span data-stu-id="7d08c-164">The full expansion generates code more like this:</span></span>

```csharp
{
    var enumerator = collection.GetEnumerator();
    try 
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally 
    {
        // dispose of enumerator.
    }
}
```

<span data-ttu-id="7d08c-165">A maneira na qual o enumerador é descartado depende das características do tipo de `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="7d08c-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="7d08c-166">Em geral, a cláusula `finally` expande para:</span><span class="sxs-lookup"><span data-stu-id="7d08c-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="7d08c-167">No entanto, se o tipo de `enumerator` é um tipo lacrado e não há nenhuma conversão implícita do tipo de `enumerator` para `IDisposable`, a cláusula `finally` se expande para um bloco vazio:</span><span class="sxs-lookup"><span data-stu-id="7d08c-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="7d08c-168">Se houver uma conversão implícita do tipo de `enumerator` para `IDisposable` e `enumerator` for um tipo de valor que não aceita valores nulos, a cláusula `finally` se expandirá para:</span><span class="sxs-lookup"><span data-stu-id="7d08c-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="7d08c-169">Felizmente, você não precisa se lembrar de todos esses detalhes.</span><span class="sxs-lookup"><span data-stu-id="7d08c-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="7d08c-170">A instrução `foreach` trata todas essas nuances para você.</span><span class="sxs-lookup"><span data-stu-id="7d08c-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="7d08c-171">O compilador gerará o código correto para qualquer um desses constructos.</span><span class="sxs-lookup"><span data-stu-id="7d08c-171">The compiler will generate the correct code for any of these constructs.</span></span> 


