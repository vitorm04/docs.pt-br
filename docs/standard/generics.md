---
title: Visão geral dos tipos genéricos (genéricos)
description: Saiba como os genéricos atuam como modelos de código que permitem que você defina estruturas de dados fortemente tipadas sem se comprometer com um tipo de dados real.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: f51d69088b0d5c798f3aa3a6c1f5b62b3ea81d39
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635277"
---
# <a name="generic-types-overview"></a><span data-ttu-id="85504-103">Visão geral de tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="85504-103">Generic types overview</span></span>

<span data-ttu-id="85504-104">Desenvolvedores usam genéricos o tempo todo no .NET, seja implícita ou explicitamente.</span><span class="sxs-lookup"><span data-stu-id="85504-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="85504-105">Ao usar o LINQ no .NET, você já percebeu que você está trabalhando com <xref:System.Collections.Generic.IEnumerable%601>?</span><span class="sxs-lookup"><span data-stu-id="85504-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="85504-106">Ou se você já viu uma amostra on-line de um "repositório genérico" para falar `IQueryable<T>`com bancos de dados usando o Entity Framework, você viu que a maioria dos métodos retornam?</span><span class="sxs-lookup"><span data-stu-id="85504-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="85504-107">Talvez você tenha se perguntado o que é o **T** nesses exemplos e por que ele está lá.</span><span class="sxs-lookup"><span data-stu-id="85504-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="85504-108">Introduzidos pela primeira vez no .NET Framework 2.0, os genéricos são essencialmente um "modelo de código" que permite aos desenvolvedores definir estruturas de dados [fortemente tipadas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) sem se comprometer com um tipo de dados real.</span><span class="sxs-lookup"><span data-stu-id="85504-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="85504-109">Por <xref:System.Collections.Generic.List%601> exemplo, é uma [coleção genérica](xref:System.Collections.Generic) que pode ser declarada `List<int>` `List<string>`e `List<Person>`usada com qualquer tipo, como , ou .</span><span class="sxs-lookup"><span data-stu-id="85504-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="85504-110">Para entender por que os genéricos são úteis, vamos dar uma olhada em uma classe específica antes e depois adicionar os genéricos: <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="85504-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="85504-111">No .NET Framework 1.0, os elementos `ArrayList` eram do tipo <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="85504-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="85504-112">Qualquer elemento adicionado à coleção foi silenciosamente `Object`convertido em um .</span><span class="sxs-lookup"><span data-stu-id="85504-112">Any element added to the collection was silently converted into an `Object`.</span></span> <span data-ttu-id="85504-113">O mesmo aconteceria ao ler elementos da lista.</span><span class="sxs-lookup"><span data-stu-id="85504-113">The same would happen when reading elements from the list.</span></span> <span data-ttu-id="85504-114">Esse processo é conhecido como [conversão boxing e unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md) e afeta o desempenho.</span><span class="sxs-lookup"><span data-stu-id="85504-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="85504-115">Além do desempenho, no entanto, não há como determinar o tipo de dados na lista no momento da compilação, o que torna algum código frágil.</span><span class="sxs-lookup"><span data-stu-id="85504-115">Aside from performance, however, there's no way to determine the type of data in the list at compile time, which makes for some fragile code.</span></span> <span data-ttu-id="85504-116">Genéricos resolvem esse problema definindo o tipo de dados que cada instância de lista conterá.</span><span class="sxs-lookup"><span data-stu-id="85504-116">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="85504-117">Resumindo, você só pode adicionar inteiros a `List<int>` e só pode adicionar Pessoas a `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="85504-117">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="85504-118">Os genéricos também estão disponíveis em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85504-118">Generics are also available at run time.</span></span> <span data-ttu-id="85504-119">O tempo de execução sabe que tipo de estrutura de dados você está usando e pode armazená-la na memória de forma mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="85504-119">The runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="85504-120">O exemplo a seguir é um pequeno programa que ilustra a eficiência de conhecer o tipo de estrutura de dados em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="85504-120">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

<span data-ttu-id="85504-121">Este programa produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="85504-121">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="85504-122">A primeira coisa que você pode observar aqui é que classificar a lista genérica é significativamente mais rápido do que classificar a lista não genérica.</span><span class="sxs-lookup"><span data-stu-id="85504-122">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="85504-123">Você também observará que o tipo de lista genérico é distinto ([System.Int32]) enquanto o tipo da lista não genérico é generalizado.</span><span class="sxs-lookup"><span data-stu-id="85504-123">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="85504-124">Como o tempo de `List<int>` execução <xref:System.Int32>sabe que o genérico é do tipo, ele pode armazenar os `ArrayList` elementos da lista em uma matriz inteira subjacente na memória, enquanto o não genérico tem que lançar cada elemento da lista para um objeto.</span><span class="sxs-lookup"><span data-stu-id="85504-124">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="85504-125">Como este exemplo mostra, as conversões extras levam tempo e reduzem a velocidade da classificação da lista.</span><span class="sxs-lookup"><span data-stu-id="85504-125">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="85504-126">Uma vantagem adicional de o runtime saber o tipo de seu genérico é uma melhor experiência de depuração.</span><span class="sxs-lookup"><span data-stu-id="85504-126">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="85504-127">Quando você está depurando um genérico em C#, você sabe que tipo de cada elemento está na sua estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="85504-127">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="85504-128">Sem os genéricos, você não faria ideia de qual o tipo de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="85504-128">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="85504-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="85504-129">See also</span></span>

- [<span data-ttu-id="85504-130">Guia de Programação em C# – Genéricos</span><span class="sxs-lookup"><span data-stu-id="85504-130">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
