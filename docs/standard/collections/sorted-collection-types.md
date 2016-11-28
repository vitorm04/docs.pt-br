---
title: "Tipos de coleção Sorted"
description: "Tipos de coleção Sorted"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdc9c13e-e56a-433b-a293-c92364f6e9cb
translationtype: Human Translation
ms.sourcegitcommit: 149086110d7470d97e1ab3e5969269626290b523
ms.openlocfilehash: 4359ec4c55921497f32d5891ea337a30867e4fa5

---

# <a name="sorted-collection-types"></a>Tipos de coleção Sorted  
 
 A classe [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList), a classe genérica [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) e a classe genérica [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) são semelhantes à classe [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) e à classe genérica [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) nas quais elas implementam a interface [IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary), mas elas mantêm seus elementos em ordem de classificação por chave e não têm as características de inserção e recuperação de O(1) das tabelas de hash. As três classes têm várias funcionalidades em comum:  

 *   As três classes implementam a interface [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary). As duas classes genéricas também implementam a interface genérica [System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2).  
 
 *   Cada elemento é um par chave/valor para fins de enumeração.   
  
> [!NOTE]  
> A classe não genérica [SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) retorna objetos [DictionaryEntry](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryEntry) quando é enumerada, embora os dois tipos genéricos retornem objetos [KeyValuePair&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.KeyValuePair-2).  
   
*   Os elementos são classificados de acordo com uma implementação de [System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) (para `SortedList` não genérica) ou uma implementação de [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) (para as duas classes genéricas).  
   
 *   Cada classe fornece propriedades que retornam coleções contendo apenas as chaves ou apenas os valores.  
   
A tabela a seguir lista algumas das diferenças entre as duas classes de listas classificadas e a classe [SortedDictionary<TKey, TValue>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2).  
   
 `SortedList` classe não genérica e `SortedList<TKey, TValue>` classe genérica | `SortedDictionary<TKey, TValue>` classe genérica  
 --------------------------------------------------------------------------------- | ------------------------------  
 As propriedades que retornam chaves e valores são indexadas, permitindo uma recuperação indexada eficiente. | Recuperação não indexada.  
 A recuperação é O(log n). | A recuperação é O(log n).  
 A inserção e a remoção geralmente são O(n). No entanto, a inserção é O(1) para dados que já estão na ordem de classificação, para que cada elemento seja adicionado ao final da lista. (Isso pressupõe que um redimensionamento não é necessário.) | A inserção e a remoção são O(log n).  
 Usa menos memória do que um `SortedDictionary<TKey, TValue>`. | Usa mais memória do que a classe não genérica `SortedList` e a classe genérica `SortedList<TKey, TValue>`.  
  
 Para listas ou dicionários classificados que precisam estar acessíveis simultaneamente de vários threads, você pode adicionar a lógica de classificação em uma classe derivada de [ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2).  
  
 > [!NOTE]  
 > Para valores que contêm suas próprias chaves (por exemplo, registros de funcionários que contêm um número de ID do funcionário), você pode criar uma coleção com chave que tenha algumas características de uma lista e algumas características de um dicionário, derivando de uma classe genérica [KeyedCollection&lt;TKey, TItem&gt;]().  
   
 A classe [SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) fornece uma árvore de balanceamento automático que mantém os dados em ordem classificada após inserções, exclusões e pesquisas. Essa classe e a classe [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) implementam a interface [ISet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ISet-1).  
   
## <a name="see-also"></a>Consulte também  
  
[System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)  
   
[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)  
   
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)  
 
[Tipos de Coleção de Uso Comum](commonly-used-collection-types.md) 



<!--HONumber=Nov16_HO4-->


