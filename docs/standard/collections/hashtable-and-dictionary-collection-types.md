---
title: "Tipos de coleção Hashtable e Dictionary"
description: "Tipos de coleção Hashtable e Dictionary"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0f18fac7-fd0d-4f25-a046-1d3d51de062e
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: 373948733acc883a3fdc04d8dfc34f66435362af

---

# <a name="hashtable-and-dictionary-collection-types"></a>Tipos de coleção Hashtable e Dictionary

A classe [System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) e as classes genéricas [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) e [System.Collections.Concurrent.ConcurrentDictionary<T>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) implementam a interface [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary). A classe genérica `Dictionary<T>` também implementa a interface genérica [IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2). Portanto, cada elemento nessas coleções é um par chave-valor.

Um `Hashtable` objeto consiste em buckets que contêm os elementos da coleção. Um bucket é um subgrupo virtual de elementos dentro de `Hashtable`, o que torna a pesquisa e a recuperação mais fáceis e rápidas do que na maioria das coleções. Cada bucket é associado um código hash, que é gerado usando uma função de hash e tem como base a chave do elemento.

A classe [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) genérica é uma coleção não ordenada com a finalidade de conter elementos exclusivos. 

Uma função de hash é um algoritmo que retorna um código hash numérico com base em uma chave. A chave é o valor da alguma propriedade do objeto sendo armazenado. Uma função de hash deve sempre retornar o mesmo código hash para a mesma chave. É possível para uma função de hash gerar o mesmo código hash para duas chaves diferentes, mas uma função de hash que gera um código hash exclusivo para cada chave específica resulta em um melhor desempenho ao recuperar os elementos da tabela de hash.

Cada objeto que é usado como um elemento em um `Hashtable` deve ser capaz de gerar um código hash para si mesmo usando uma implementação do método `GetHashCode`. 

Quando um objeto é adicionado a um `Hashtable`, ele é armazenado no compartimento de memória que está associado ao código hash que corresponde ao código hash do objeto. Quando um valor está sendo procurado no `Hashtable`, o código hash é gerado para esse valor e o bucket associado a esse código hash é pesquisado.

Por exemplo, uma função de hash para uma cadeia de caracteres pode pegar os códigos ASCII de cada caractere na cadeia e adicioná-los em conjunto para gerar um código hash. A cadeia de caracteres "piquenique" teria um código hash diferente daquele da cadeia de caracteres "cesta"; portanto, as cadeias de caracteres "piquenique" e "cesta" ficariam em buckets diferentes. Por outro lado, "stressed" e "desserts" teriam o mesmo código hash e ficariam no mesmo bucket.

As classes `Dictionary<T>` e `ConcurrentDictionary<T>` têm a mesma funcionalidade que a classe `Hashtable`. Um `Dictionary<T>` de um tipo específico (diferente de `Object`) fornece desempenho melhor do que um `Hashtable` para tipos de valor. Isso ocorre porque os elementos de `Hashtable` são do tipo `Object`; portanto, conversões boxing e unboxing normalmente ocorrem quando você armazena ou recupera um tipo de valor. A classe `ConcurrentDictionary<T>` deve ser usada quando vários threads podem estar acessando a coleção simultaneamente.

## <a name="see-also"></a>Consulte também

[Tabela de hash](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)

[IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[Dicionário](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2)

[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)

[Tipos de Coleção de Uso Comum](commonly-used-collection-types.md)




<!--HONumber=Dec16_HO1-->


