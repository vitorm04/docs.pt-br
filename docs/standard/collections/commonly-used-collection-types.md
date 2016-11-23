---
title: "Tipos de coleção de uso comum"
description: "Tipos de coleção de uso comum"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 55861611-1e40-4cc2-9ec5-0b2df4ba6c0c
translationtype: Human Translation
ms.sourcegitcommit: d4e7ef84480aa9f735fb8d1ff03c9e8a61127c83
ms.openlocfilehash: 6cadcd91810f08900b58e402240e8a469fad2018

---

# <a name="commonly-used-collection-types"></a>Tipos de coleção de uso comum

Tipos de coleção são as variações comuns de coleções de dados, como tabelas de hash, filas, pilhas, pacotes, dicionários e listas.

Coleções são baseadas nas interfaces [`ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection), [`IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList), [`IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) ou em seus equivalentes genéricos. As interfaces `IList` e `IDictionary` são ambas derivadas da interface `ICollection`; portanto, todas as coleções são baseadas na interface `ICollection` direta ou indiretamente. Em coleções baseadas na interface `IList` (como, [`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array), [`ArrayList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) ou [`List<T>)`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1)) ou diretamente na interface `ICollection` (como [`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue), [`ConcurrentQueue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1), [`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack), [`ConcurrentStack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) ou [`LinkedList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1)), cada elemento contém apenas um valor. Em coleções baseadas na interface `IDictionary` (como as classes [`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) e [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList), as classes genéricas [`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) e [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2)) ou as classes [`ConcurrentDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2), cada elemento contém uma chave e um valor. A classe [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) é exclusiva, pois ela é uma lista de valores com chaves incorporadas aos valores e, portanto, se comporta como uma lista e como um dicionário.

Coleções genéricas são a melhor solução para tipagem forte. No entanto, se o idioma não der suporte a genéricos, o namespace [`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections) incluirá coleções base, como [`CollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase), [`ReadOnlyCollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase) e [`DictionaryBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryBase), que são classes base abstratas que podem ser estendidas para criar classes de coleção que são fortemente tipadas. Quando for necessário acesso de coleção com multithread eficiente, use as coleções genéricas no namespace [`System.Collections.Concurrent`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent).

As coleções podem variar, dependendo de como os elementos são armazenados, como são classificados, como as pesquisas são executadas e como são feitas comparações. A classe [`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue) e a classe genérica [`Queue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) fornecem listas primeiro a entrar, primeiro a sair, enquanto a classe [`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack) e a classe genérica [`Stack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) fornecem listas último a entrar, primeiro a sair. A classe [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) e a classe genérica [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) fornecem versões classificadas da classe [`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) e da classe genérica [`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2). Os elementos de uma `Hashtable` ou uma `Dictionary<TKey, TValue>` são acessíveis somente pela chave do elemento, mas os elementos de uma `SortedList` ou uma [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) são acessíveis pela chave ou pelo índice do elemento. Os índices em todas as coleções são baseados em zero, exceto [`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array), que permite matrizes que não sejam baseadas em zero.

O recurso LINQ to Objects permite que você use consultas LINQ para acessar objetos na memória, desde que o tipo de objeto implemente [`IEnumerable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [`IEnumerable<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1). Consultas LINQ fornecem um padrão comum para acessar dados. Elas são, geralmente, mais concisas e legíveis que os loops foreach padrão e fornecem recursos de filtragem, classificação e agrupamento. Consultas LINQ também podem melhorar o desempenho.

## <a name="related-topics"></a>Tópicos relacionados

Título | Descrição
----- | -----------
[`Collections and Data Structures`](index.md) | Discute os vários tipos de coleção disponíveis no .NET Framework, incluindo pilhas, filas, listas, matrizes e dicionários.
[`Hashtable and Dictionary Collection Types`](hashtable-and-dictionary-collection-types.md) | Descreve os recursos de tipos de dicionário baseado em hash genérico e não genérico.
[`Sorted Collection Types`](sorted-collection-types.md) | Descreve as características e o desempenho de coleções classificadas.

## <a name="reference"></a>Referência

[`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[`System.Collections.Generic`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[`System.Collections.ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection)

[`System.Collections.Generic.ICollection<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1)

[`System.Collections.IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList)

[`System.Collections.Generic.IList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1)

[`System.Collections.IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[`System.Collections.Generic.IDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[`System.Linq`](https://docs.microsoft.com/dotnet/core/api/System.Linq)



<!--HONumber=Nov16_HO4-->


