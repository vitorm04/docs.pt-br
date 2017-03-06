---
title: "Quando usar coleções genéricas"
description: "Quando usar coleções genéricas"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 971e08bd-b63f-4832-9e61-9f65cbedd352
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: bde317c165981775330e1d0d8261d355e2401bc9
ms.lasthandoff: 03/03/2017

---

# <a name="when-to-use-generic-collections"></a>Quando usar coleções genéricas

Geralmente é recomendável usar coleções genéricas, porque você obtém a vantagem imediata da segurança de tipos sem precisar derivar de um tipo de coleção base e implementar membros específicos do tipo. Tipos de coleção genérica também geralmente executam melhor do que os tipos de coleção não genérica correspondentes (e melhor do que tipos que são derivados de tipos de coleção base não genérica) quando os elementos da coleção forem tipos de valor, pois com genéricos não é necessário colocar os elementos em caixa. 

Você deve usar as classes de coleção genérica no namespace [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) quando vários threads puderem adicionar ou remover itens da coleção simultaneamente.

Os seguintes tipos genéricos correspondem aos tipos de coleção existentes: 

*   [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) é a classe genérica que corresponde à [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList).

*   [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) e [ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) são as classes genéricas que correspondem a [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable). 

*   [Collection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.Collection-1) é a classe genérica que corresponde à [CollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase). `Collection<T>` pode ser usada como uma classe base, mas ao contrário de `CollectionBase`, ela não é abstrata. Isso facilita muito o seu uso.

*   [ReadOnlyCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ReadOnlyCollection-1) é a classe genérica que corresponde à [ReadOnlyCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase). `ReadOnlyCollection<T>` não é abstrata e tem um construtor que facilita expor uma [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) existente como uma coleção somente leitura.

*   As classes genéricas [Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1), [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1), [Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1), [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) e [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) correspondem às respectivas classes não genéricas com os mesmos nomes.

## <a name="additional-types"></a>Tipos adicionais

Vários tipos de coleção genérica não têm equivalentes não genéricas. Elas incluem o seguinte: 

*   [LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) é uma lista vinculada de uso geral que fornece operações de inserção e remoção O(1).

*   [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) é um dicionário classificado com operações de inserção e recuperação O(log n), o que o torna uma alternativa útil para [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2). 

*   [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) é um híbrido entre uma lista e um dicionário, que fornece uma maneira de armazenar objetos que contenham suas próprias chaves.

*   [BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) implementa uma classe de coleção com funcionalidade de delimitação e bloqueio.

*   [ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) fornece rápida inserção e remoção de elementos não classificados.

## <a name="linq-to-objects"></a>Objetos LINQ to

O recurso LINQ to Objects permite que você use consultas LINQ para acessar objetos na memória desde que o tipo de objeto implemente a interface [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1). Consultas LINQ fornecem um padrão comum para acessar dados; são geralmente mais concisas e legíveis que os loops `foreach` padrão; e fornecem recursos de filtragem, classificação e agrupamento. Consultas LINQ também podem melhorar o desempenho.

## <a name="additional-functionality"></a>Funcionalidade adicional

Alguns dos tipos genéricos têm funcionalidades que não se encontram em tipos de coleção não genérica. Por exemplo, a classe [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1), que corresponde à classe [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) não genérica, tem vários métodos que aceitam delegados genéricos, tais como o delegado [Predicate&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Predicate-1) que permite que você especifique métodos para pesquisa na lista e o delegado [Action&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Action-1) que representa métodos que atuam em cada elemento da lista.

A classe [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) permite que você especifique suas próprias implementações de interface genérica [IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) para classificação e pesquisa na lista. As classes [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) e [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) também têm essa funcionalidade. Além disso, essas classes permitem que você especifique comparadores quando a coleção for criada. De maneira semelhante, as classes [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) e [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) permitem que você especifique seus próprios comparadores de igualdade.

## <a name="see-also"></a>Consulte também

[Coleções e Estruturas de Dados](index.md) 

[Tipos de Coleção de Uso Comum](commonly-used-collection-types.md)

