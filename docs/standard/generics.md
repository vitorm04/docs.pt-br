---
title: "Visão Geral dos Tipos Genéricos (Genéricos)"
description: "Visão Geral dos Tipos Genéricos (Genéricos)"
keywords: .NET, .NET Core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
translationtype: Human Translation
ms.sourcegitcommit: 5b1a76c011b95db3ff5c4b4e01556f79c45fb369
ms.openlocfilehash: 09f52c2b4b821b21279f602e7bbf45e91fe98dec

---

# <a name="generic-types-generics-overview"></a>Visão Geral dos Tipos Genéricos (Genéricos)

Usamos genéricos sempre em C#, de forma implícita ou explícita. Ao usar LINQ em C#, você já percebeu alguma vez estar trabalhando com IEnumerable<T>? Ou, no caso de você já ter visto um exemplo de um "repositório genérico" online para conversar com bancos de dados usando o Entity Framework, você já viu que a maioria dos métodos retornam IQueryable<T>? Talvez você tenha se perguntdo o que é o **T** nesses exemplos e por que ele está lá?

Introduzida pela primeira vez no .NET Framework 2.0, os genéricos envolviam alterações tanto à linguagem C# quanto CLR (Common Language Runtime). **Genéricos** são essencialmente um "modelo de código" que permite que os desenvolvedores definam estruturas de dados [fortemente tipadas](https://msdn.microsoft.com/library/hbzz1a9a.aspx) sem se comprometer com um tipo de dados real. Por exemplo, `List<T>` é uma [coleção de genéricos](https://msdn.microsoft.com/library/System.Collections.Generic.aspx) que pode ser declarada e usada com qualquer tipo: `List<int>`, `List<string>`, `List<Person>`, etc.

Então, do que isso realmente se trata? Por que os genéricos são úteis? Para compreender isso, precisamos dar uma olhada em uma classe específica antes e depois de adicionar os genéricos. Vamos examinar o `ArrayList`. No C# 1.0, os elementos `ArrayList` eram do tipo `object`. Isso significava que qualquer elemento que fosse adicionado silenciosamente era convertido em um `object`; a mesma coisa acontece ao ler os elementos da lista (esse processo é conhecido como [conversão boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) e conversão unboxing, respectivamente). Conversões boxing e unboxing têm um impacto sobre o desempenho. Mais importante do que isso, no entanto, não há uma maneira de saber, durante o tempo de compilação, qual é o tipo real dos dados na lista. Isso resulta em um código frágil. Genéricos resolvem esse problema, fornecendo informações adicionais sobre o tipo de dados que cada instância da lista conterá. Resumindo, você só pode adicionar inteiros a `List<int>` e só pode adicionar pessoas a `List<Person>`, etc.

Genéricos também estão disponíveis em tempo de execução ou **reificados**. Isso significa que o tempo de execução sabe que tipo de estrutura de dados você está usando e pode armazená-la na memória com mais eficiência.

Aqui está um pequeno programa que ilustra a eficiência de saber o tipo da estrutura de dados em tempo de execução:

```cs
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

Este programa produz a seguinte saída:

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms

```

A primeira coisa que você observa aqui é que classificar a lista genérica é significativamente mais rápido do que classificar a lista não genérica. Você também observará que o tipo de lista genérico é distinto ([System.Int32]) enquanto o tipo da lista não genérico é generalizado. Como o tempo de execução sabe que o genérico `List<int>` é do tipo int, ele pode armazenar elementos de lista em uma matriz de inteiros subjacente na memória, enquanto o `ArrayList` não genérico tem que converter cada elemento da lista como um objeto armazenado em uma matriz de objetos na memória. Conforme mostrado neste exemplo, as conversões extras levam tempo e atrasam a classificação da lista.

A última coisa útil sobre o tempo de execução saber o tipo de seu genérico é uma melhor experiência de depuração. Quando você está depurando um genérico em C#, você sabe que tipo de cada elemento está na sua estrutura de dados. Sem os genéricos, você não faria ideia de qual o tipo de cada elemento.

## <a name="further-reading-and-resources"></a>Recursos e leituras adicionais

*   [Introdução aos genéricos C#](https://msdn.microsoft.com/library/ms379564.aspx)
*   [Guia de Programação em C# – Genéricos](https://msdn.microsoft.com/library/512aeb7t.aspx)



<!--HONumber=Dec16_HO1-->


