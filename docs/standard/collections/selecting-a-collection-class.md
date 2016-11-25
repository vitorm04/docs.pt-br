---
title: "Selecionando uma classe de coleção"
description: "Selecionando uma classe de coleção"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0a60fca7-e082-48d4-9dda-30b0d3e67ec7
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: 38f5a970738103bd96c9570f4d6e8ee540af6ee1

---

# <a name="selecting-a-collection-class"></a>Selecionando uma classe de coleção

Certifique-se de escolher sua classe de coleção com cuidado. A utilização do tipo errado pode restringir o uso da coleção. As versões genéricas e simultâneas das coleções são as preferíveis devido à maior segurança de tipo e outras melhorias. Em geral, evite usar os tipos no namespace System.Collections a menos que se direcione especificamente para o .NET Framework versão 1.1. 

Considere as perguntas a seguir:

* Você precisa de uma lista sequencial em que o elemento normalmente será descartado após seu valor ser recuperado? 

    * Em caso afirmativo, considere a possibilidade de usar a classe genérica [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) caso precise do comportamento PEPS (primeiro a entrar, primeiro a sair). Considere a possibilidade de usar a classe genérica [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) caso precise do comportamento LIFO (último a entrar, primeiro a sair). Para obter acesso seguro de vários threads, use as versões simultâneas [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) e [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1).
    
    * Caso contrário, considere a possibilidade de usar outras coleções.
    
* Você precisa acessar os elementos em uma ordem específica, como PEPS, UEPS ou aleatória?

    * O [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) ou a classe genérica [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) oferecem acesso PEPS. Para obter mais informações, consulte [Quando usar uma coleção thread-safe](threadsafe/when-to-use-a-thread-safe-collection.md).
    
    * O [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) ou a classe genérica [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) oferecem acesso LIFO. Para obter mais informações, consulte [Quando usar uma coleção thread-safe](threadsafe/when-to-use-a-thread-safe-collection.md).
    
    * A classe genérica [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) possibilita acesso sequencial do início ao fim ou do fim ao início.
    
* Você precisa acessar cada elemento pelo índice? 

    * A classe [System.Collections.Specialized.StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) e a classe genérica [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) oferecem acesso aos seus elementos pelo índice com base zero do elemento. 
    
    * As classes [System.Collections.Specialized.ListDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.ListDictionary) e [System.Collections.Specialized.StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary) e as classes genéricas [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) e [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) oferecem acesso aos seus elementos pela chave do elemento.
    
    * As classes [System.Collections.Specialized.NameObjectCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameObjectCollectionBase) e [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection) e as classes genéricas [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) e [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) oferecem acesso aos seus elementos pelo índice com base zero ou a chave do elemento.
    
* Cada elemento conterá um valor, uma combinação de uma chave e um valor ou uma combinação de uma chave e diversos valores? 

    * Um valor: use qualquer uma das coleções com base na interface genérica [System.Collections.Generic.IList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1).
    
    * Uma chave e um valor: use qualquer uma das coleções com base na interface genérica [System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2).
    
    * Um valor com chave embutida: use a classe genérica [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2).
    
    * Uma chave e diversos valores: use a classe [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection).
    
* Você precisa classificar os elementos de forma diferente de como foram inseridos? 

    * A classe [System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) classifica seus elementos pelos códigos hash.
    
    * As classes genéricas [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) e [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) classificam seus elementos pela chave, com base nas implementações da interface [System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) e da interface genérica [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1).
    
    * A classe genérica [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) fornece um método `Sort` que pega uma implementação da interface genérica `IComparer<T>` como parâmetro.
    
* Você precisa de coleções que aceitem apenas cadeias de caracteres? 

    * [StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) (com base em [System.Collections.IList](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList)) e [StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary) (com base em [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)) estão no namespace [System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized). 
    
    * Além disso, é possível usar qualquer uma das classes genéricas de coleção no namespace [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) como coleções de cadeias de caracteres fortemente tipadas especificando a classe `String` para seus argumentos de tipo genérico.
    
## <a name="linq-to-objects"></a>Objetos LINQ to

O LINQ to Objects permite que os desenvolvedores usem consultas LINQ para acessar objetos na memória desde que o tipo de objeto implemente [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1). As consultas LINQ fornecem um padrão comum para acessar dados. Em geral, elas são mais concisas e legíveis que os loops foreach padrão e fornecem recursos de filtragem, classificação e agrupamento. Para obter mais informações, consulte [LINQ (Consulta Integrada à Linguagem)](../../csharp/linq.md).

## <a name="see-also"></a>Consulte também

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[Coleções Thread-Safe](threadsafe/index.md)



<!--HONumber=Nov16_HO3-->


