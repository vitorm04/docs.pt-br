---
title: Iteradores
description: "Saiba como usar iteradores C# internos e como criar seus próprios métodos iteradores personalizados."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 18a5819402c752f32aecd0cd4c3bd5a490292ebf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iterators"></a><span data-ttu-id="b4b4a-104">Iteradores</span><span class="sxs-lookup"><span data-stu-id="b4b4a-104">Iterators</span></span>

<span data-ttu-id="b4b4a-105">Quase todos os programas que você escrever terão alguma necessidade de iterar em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-105">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="b4b4a-106">Você escreverá um código que examina cada item em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-106">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="b4b4a-107">Você também criará métodos de iterador que são métodos que produzem um iterador para os elementos dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-107">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="b4b4a-108">Eles podem ser usados para:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-108">These can be used for:</span></span>

+ <span data-ttu-id="b4b4a-109">Executar uma ação em cada item em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-109">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="b4b4a-110">Enumerar uma coleção personalizada.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-110">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="b4b4a-111">Estender [LINQ](linq/index.md) ou outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-111">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="b4b4a-112">Criar um pipeline de dados em que os dados fluem com eficiência pelos métodos de iterador.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-112">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="b4b4a-113">A linguagem C# fornece recursos para esses dois cenários.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-113">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="b4b4a-114">Este artigo fornece uma visão geral desses recursos.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-114">This article provides an overview of those features.</span></span>

<span data-ttu-id="b4b4a-115">Este tutorial tem várias etapas.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-115">This tutorial has multiple steps.</span></span> <span data-ttu-id="b4b4a-116">Após cada etapa, você poderá executar o aplicativo e ver o progresso.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-116">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="b4b4a-117">Você também pode [exibir ou baixar o exemplo concluído](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-117">You can also [view or download the completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) for this topic.</span></span> <span data-ttu-id="b4b4a-118">Para obter instruções de download, consulte [Exemplos e tutoriais](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b4b4a-118">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="b4b4a-119">iterando com foreach</span><span class="sxs-lookup"><span data-stu-id="b4b4a-119">Iterating with foreach</span></span>

<span data-ttu-id="b4b4a-120">Enumerar uma coleção é simples: a palavra-chave `foreach` enumera uma coleção, executando a instrução inserida uma vez para cada elemento na coleção:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-120">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="b4b4a-121">E isso é tudo.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-121">That's all there is to it.</span></span> <span data-ttu-id="b4b4a-122">Para iterar em todo o conteúdo de uma coleção, a instrução `foreach` é tudo o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-122">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="b4b4a-123">No entanto, a instrução `foreach` não é mágica.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-123">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="b4b4a-124">Ele se baseia em duas interfaces genéricas definidas na biblioteca do .NET Core para gerar o código necessário para iterar uma coleção: `IEnumerable<T>` e `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-124">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="b4b4a-125">Esse mecanismo é explicado mais detalhadamente abaixo.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-125">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="b4b4a-126">Essas duas interfaces também têm contrapartes não genéricas: `IEnumerable` e `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-126">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="b4b4a-127">As versões [genéricas](programming-guide/generics/index.md) são preferenciais para o código moderno.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-127">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="b4b4a-128">Fontes de enumeração com métodos de iterador</span><span class="sxs-lookup"><span data-stu-id="b4b4a-128">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="b4b4a-129">Outro ótimo recurso da linguagem C# permite que você crie métodos que criam uma fonte para uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-129">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="b4b4a-130">Eles são chamados de *métodos de iterador*.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-130">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="b4b4a-131">Um método de iterador define como gerar os objetos em uma sequência quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-131">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="b4b4a-132">Você usa as palavras-chave contextuais `yield return` para definir um método iterador.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-132">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="b4b4a-133">Você poderia escrever esse método para produzir a sequência de inteiros de 0 a 9:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-133">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="b4b4a-134">O código acima mostra instruções `yield return` distintas para destacar o fato de que você pode usar várias instruções `yield return` discretas em um método iterador.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-134">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="b4b4a-135">Você pode (e frequentemente o faz) usar outros constructos de linguagem para simplificar o código de um método iterador.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-135">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="b4b4a-136">A definição do método abaixo produz a mesma sequência exata de números:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-136">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="b4b4a-137">Você não precisa determinar uma ou a outra.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-137">You don't have to decide one or the other.</span></span> <span data-ttu-id="b4b4a-138">Você pode ter quantas instruções `yield return` forem necessárias para atender as necessidades do seu método:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-138">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="b4b4a-139">Essa é a sintaxe básica.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-139">That's the basic syntax.</span></span> <span data-ttu-id="b4b4a-140">Vamos considerar um exemplo do mundo real em que você escreveria um método iterador.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-140">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="b4b4a-141">Imagine que você está em um projeto de IoT e os sensores de dispositivo geram um enorme fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-141">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="b4b4a-142">Para ter uma noção dos dados, você pode escrever um método realiza a amostragem a cada N elementos de dados.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-142">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="b4b4a-143">Esse pequeno método iterador resolve:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-143">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="b4b4a-144">Há uma restrição importante em métodos de iterador: você não pode ter uma instrução `return` e uma instrução `yield return` no mesmo método.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-144">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="b4b4a-145">O seguinte não compilará:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-145">The following will not compile:</span></span>

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

<span data-ttu-id="b4b4a-146">Essa restrição normalmente não é um problema.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-146">This restriction normally isn't a problem.</span></span> <span data-ttu-id="b4b4a-147">Você tem a opção de usar `yield return` em todo o método ou separar o método original em vários métodos, alguns usando `return` e alguns usando `yield return`.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-147">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="b4b4a-148">Você pode modificar um pouco o último método para usar `yield return` em todos os lugares:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-148">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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
 
<span data-ttu-id="b4b4a-149">Às vezes, a resposta certa é dividir um método iterador em dois métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-149">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="b4b4a-150">Um que usa `return` e outro que usa `yield return`.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-150">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="b4b4a-151">Considere uma situação em que você talvez queira retornar uma coleção vazia ou os primeiros cinco números ímpares, com base em um argumento booliano.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-151">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="b4b4a-152">Você poderia escrever isso como esses dois métodos:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-152">You could write that as these two methods:</span></span>

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
 
<span data-ttu-id="b4b4a-153">Observe os métodos acima.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-153">Look at the methods above.</span></span> <span data-ttu-id="b4b4a-154">O primeiro usa a instrução `return` padrão para retornar uma coleção vazia ou o iterador criado pelo segundo método.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-154">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="b4b4a-155">O segundo método usa a instrução `yield return` para criar a sequência solicitada.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-155">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="b4b4a-156">Aprofundamento em `foreach`</span><span class="sxs-lookup"><span data-stu-id="b4b4a-156">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="b4b4a-157">A instrução `foreach` se expande em uma expressão padrão que usa as interfaces `IEnumable<T>` e `IEnumerator<T>` para iterar em todos os elementos de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-157">The `foreach` statement expands into a standard idiom that uses the `IEnumable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="b4b4a-158">Ela também minimiza os erros cometidos pelos desenvolvedores por não gerenciarem os recursos adequadamente.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-158">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="b4b4a-159">O compilador converte o loop `foreach` mostrado no primeiro exemplo em algo semelhante a esse constructo:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-159">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="b4b4a-160">O constructo acima representa o código gerado pelo compilador C# da versão 5 e posterior.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-160">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="b4b4a-161">Antes da versão 5, a variável `item` tinha um escopo diferente:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-161">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="b4b4a-162">Isso foi alterado porque o comportamento anterior poderia levar a bugs sutis e difíceis de diagnosticar envolvendo expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-162">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="b4b4a-163">Consulte a seção sobre [expressões lambda](lambda-expressions.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-163">See the section on [lambda expressions](lambda-expressions.md) for more information.</span></span> 

<span data-ttu-id="b4b4a-164">O código exato gerado pelo compilador é um pouco mais complicada e lida com situações em que o objeto retornado por `GetEnumerator()` implementa a interface `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-164">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="b4b4a-165">A expansão completa gera um código mais semelhante a esse:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-165">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="b4b4a-166">A maneira na qual o enumerador é descartado depende das características do tipo de `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-166">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="b4b4a-167">Em geral, a cláusula `finally` expande para:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-167">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="b4b4a-168">No entanto, se o tipo de `enumerator` é um tipo lacrado e não há nenhuma conversão implícita do tipo de `enumerator` para `IDisposable`, a cláusula `finally` se expande para um bloco vazio:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-168">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="b4b4a-169">Se houver uma conversão implícita do tipo de `enumerator` para `IDisposable` e `enumerator` for um tipo de valor que não aceita valores nulos, a cláusula `finally` se expandirá para:</span><span class="sxs-lookup"><span data-stu-id="b4b4a-169">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="b4b4a-170">Felizmente, você não precisa se lembrar de todos esses detalhes.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-170">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="b4b4a-171">A instrução `foreach` trata todas essas nuances para você.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-171">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="b4b4a-172">O compilador gerará o código correto para qualquer um desses constructos.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-172">The compiler will generate the correct code for any of these constructs.</span></span> 


