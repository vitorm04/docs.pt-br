---
title: Visão geral dos tipos genéricos (genéricos)
description: Saiba como os genéricos atuam como modelos de código que permitem que você defina estruturas de dados fortemente tipadas sem se comprometer com um tipo de dados real.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 0188e620a45462e7cc31391406ade9d57b1b0220
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588477"
---
# <a name="generic-types-overview"></a>Visão geral de tipos genéricos

Desenvolvedores usam genéricos o tempo todo no .NET, seja implícita ou explicitamente. Ao usar o LINQ no .NET, você já percebeu que você está trabalhando com <xref:System.Collections.Generic.IEnumerable%601>? Ou se você já viu uma amostra on-line de um "repositório genérico" para falar `IQueryable<T>`com bancos de dados usando o Entity Framework, você viu que a maioria dos métodos retornam? Talvez você tenha se perguntado o que é o **T** nesses exemplos e por que ele está lá.

Introduzidos pela primeira vez no .NET Framework 2.0, os genéricos são essencialmente um "modelo de código" que permite aos desenvolvedores definir estruturas de dados [fortemente tipadas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) sem se comprometer com um tipo de dados real. Por <xref:System.Collections.Generic.List%601> exemplo, é uma [coleção genérica](xref:System.Collections.Generic) que pode ser declarada `List<int>` `List<string>`e `List<Person>`usada com qualquer tipo, como , ou .

Para entender por que os genéricos são úteis, vamos dar uma olhada em uma classe específica antes e depois adicionar os genéricos: <xref:System.Collections.ArrayList>. No .NET Framework 1.0, os elementos `ArrayList` eram do tipo <xref:System.Object>. Isso significava que qualquer elemento adicionado silenciosamente era convertido em um `Object`. O mesmo aconteceria ao ler os elementos da lista. Esse processo é conhecido como [conversão boxing e unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md) e afeta o desempenho. Mais do que isso, no entanto, não é possível determinar o tipo de dados na lista no tempo de compilação. Isso resulta em um código frágil. Genéricos resolvem esse problema definindo o tipo de dados que cada instância de lista conterá. Resumindo, você só pode adicionar inteiros a `List<int>` e só pode adicionar Pessoas a `List<Person>`.

Os genéricos também estão disponíveis em tempo de execução. Isso significa que o runtime sabe que tipo de estrutura de dados você está usando e pode armazená-la na memória com mais eficiência.

O exemplo a seguir é um pequeno programa que ilustra a eficiência de conhecer o tipo de estrutura de dados em tempo de execução:

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

Este programa produz uma saída semelhante à seguinte:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

A primeira coisa que você pode observar aqui é que classificar a lista genérica é significativamente mais rápido do que classificar a lista não genérica. Você também observará que o tipo de lista genérico é distinto ([System.Int32]) enquanto o tipo da lista não genérico é generalizado. Como o tempo de `List<int>` execução <xref:System.Int32>sabe que o genérico é do tipo, ele pode armazenar os `ArrayList` elementos da lista em uma matriz inteira subjacente na memória, enquanto o não genérico tem que lançar cada elemento da lista para um objeto. Como este exemplo mostra, as conversões extras levam tempo e reduzem a velocidade da classificação da lista.

Uma vantagem adicional de o runtime saber o tipo de seu genérico é uma melhor experiência de depuração. Quando você está depurando um genérico em C#, você sabe que tipo de cada elemento está na sua estrutura de dados. Sem os genéricos, você não faria ideia de qual o tipo de cada elemento.

## <a name="see-also"></a>Confira também

- [Guia de Programação em C# – Genéricos](../../docs/csharp/programming-guide/generics/index.md)
