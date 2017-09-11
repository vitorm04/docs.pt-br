---
title: "Visão Geral dos Tipos Genéricos (Genéricos)"
description: "Saiba como os genéricos atuam como modelos de código que permitem que você defina estruturas de dados fortemente tipadas sem se comprometer com um tipo de dados real."
keywords: .NET, .NET Core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.translationtype: HT
ms.sourcegitcommit: 75642ff3beb4462faa9068db76c89f3cb5f75ab8
ms.openlocfilehash: 08b8de2fe17a0032a1c1180667f39b1d6ce0feb6
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---

# <a name="generic-types-generics-overview"></a><span data-ttu-id="7b649-104">Visão Geral dos Tipos Genéricos (Genéricos)</span><span class="sxs-lookup"><span data-stu-id="7b649-104">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="7b649-105">Usamos genéricos sempre em C#, de forma implícita ou explícita.</span><span class="sxs-lookup"><span data-stu-id="7b649-105">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="7b649-106">Ao usar LINQ em C#, você já percebeu alguma vez estar trabalhando com IEnumerable<T>?</span><span class="sxs-lookup"><span data-stu-id="7b649-106">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="7b649-107">Ou, no caso de você já ter visto um exemplo de um "repositório genérico" online para conversar com bancos de dados usando o Entity Framework, você já viu que a maioria dos métodos retornam IQueryable<T>?</span><span class="sxs-lookup"><span data-stu-id="7b649-107">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="7b649-108">Talvez você tenha se perguntdo o que é o **T** nesses exemplos e por que ele está lá?</span><span class="sxs-lookup"><span data-stu-id="7b649-108">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="7b649-109">Introduzida pela primeira vez no .NET Framework 2.0, os genéricos envolviam alterações tanto à linguagem C# quanto CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="7b649-109">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="7b649-110">**Genéricos** são essencialmente um "modelo de código" que permite que os desenvolvedores definam estruturas de dados [fortemente tipadas](https://msdn.microsoft.com/library/hbzz1a9a.aspx) sem se comprometer com um tipo de dados real.</span><span class="sxs-lookup"><span data-stu-id="7b649-110">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="7b649-111">Por exemplo, `List<T>` é uma [coleção de genéricos](xref:System.Collections.Generic) que pode ser declarada e usada com qualquer tipo: `List<int>`, `List<string>`, `List<Person>`, etc.</span><span class="sxs-lookup"><span data-stu-id="7b649-111">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="7b649-112">Então, do que isso realmente se trata?</span><span class="sxs-lookup"><span data-stu-id="7b649-112">So, what’s the point?</span></span> <span data-ttu-id="7b649-113">Por que os genéricos são úteis?</span><span class="sxs-lookup"><span data-stu-id="7b649-113">Why are generics useful?</span></span> <span data-ttu-id="7b649-114">Para compreender isso, precisamos dar uma olhada em uma classe específica antes e depois de adicionar os genéricos.</span><span class="sxs-lookup"><span data-stu-id="7b649-114">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="7b649-115">Vamos examinar o `ArrayList`.</span><span class="sxs-lookup"><span data-stu-id="7b649-115">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="7b649-116">No C# 1.0, os elementos `ArrayList` eram do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="7b649-116">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="7b649-117">Isso significava que qualquer elemento que fosse adicionado silenciosamente era convertido em um `object`; a mesma coisa acontece ao ler os elementos da lista (esse processo é conhecido como [conversão boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) e conversão unboxing, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="7b649-117">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) and unboxing respectively).</span></span> <span data-ttu-id="7b649-118">Conversões boxing e unboxing têm um impacto sobre o desempenho.</span><span class="sxs-lookup"><span data-stu-id="7b649-118">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="7b649-119">Mais importante do que isso, no entanto, não há uma maneira de saber, durante o tempo de compilação, qual é o tipo real dos dados na lista.</span><span class="sxs-lookup"><span data-stu-id="7b649-119">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="7b649-120">Isso resulta em um código frágil.</span><span class="sxs-lookup"><span data-stu-id="7b649-120">This makes for some fragile code.</span></span> <span data-ttu-id="7b649-121">Genéricos resolvem esse problema, fornecendo informações adicionais sobre o tipo de dados que cada instância da lista conterá.</span><span class="sxs-lookup"><span data-stu-id="7b649-121">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="7b649-122">Resumindo, você só pode adicionar inteiros a `List<int>` e só pode adicionar pessoas a `List<Person>`, etc.</span><span class="sxs-lookup"><span data-stu-id="7b649-122">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="7b649-123">Genéricos também estão disponíveis em tempo de execução ou **reificados**.</span><span class="sxs-lookup"><span data-stu-id="7b649-123">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="7b649-124">Isso significa que o tempo de execução sabe que tipo de estrutura de dados você está usando e pode armazená-la na memória com mais eficiência.</span><span class="sxs-lookup"><span data-stu-id="7b649-124">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="7b649-125">Aqui está um pequeno programa que ilustra a eficiência de saber o tipo da estrutura de dados em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="7b649-125">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="7b649-126">Este programa produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="7b649-126">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="7b649-127">A primeira coisa que você observa aqui é que classificar a lista genérica é significativamente mais rápido do que classificar a lista não genérica.</span><span class="sxs-lookup"><span data-stu-id="7b649-127">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="7b649-128">Você também observará que o tipo de lista genérico é distinto ([System.Int32]) enquanto o tipo da lista não genérico é generalizado.</span><span class="sxs-lookup"><span data-stu-id="7b649-128">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="7b649-129">Como o tempo de execução sabe que o genérico `List<int>` é do tipo int, ele pode armazenar elementos de lista em uma matriz de inteiros subjacente na memória, enquanto o `ArrayList` não genérico tem que converter cada elemento da lista como um objeto armazenado em uma matriz de objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="7b649-129">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="7b649-130">Conforme mostrado neste exemplo, as conversões extras levam tempo e atrasam a classificação da lista.</span><span class="sxs-lookup"><span data-stu-id="7b649-130">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="7b649-131">A última coisa útil sobre o tempo de execução saber o tipo de seu genérico é uma melhor experiência de depuração.</span><span class="sxs-lookup"><span data-stu-id="7b649-131">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="7b649-132">Quando você está depurando um genérico em C#, você sabe que tipo de cada elemento está na sua estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="7b649-132">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="7b649-133">Sem os genéricos, você não faria ideia de qual o tipo de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="7b649-133">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="7b649-134">Recursos e leituras adicionais</span><span class="sxs-lookup"><span data-stu-id="7b649-134">Further reading and resources</span></span>

*   [<span data-ttu-id="7b649-135">Introdução aos genéricos C#</span><span class="sxs-lookup"><span data-stu-id="7b649-135">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="7b649-136">Guia de Programação em C# – Genéricos</span><span class="sxs-lookup"><span data-stu-id="7b649-136">C# Programming Guide - Generics</span></span>](https://msdn.microsoft.com/library/512aeb7t.aspx)

