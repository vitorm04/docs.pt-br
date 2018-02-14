---
title: "Selecionando uma classe de coleção"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 05339b829262a6b9b3a0265e4fbd444c6d586ea3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="selecting-a-collection-class"></a>Selecionando uma classe de coleção
Certifique-se de escolher sua classe de coleção com cuidado. A utilização do tipo errado pode restringir o uso da coleção. Em geral, evite usar os tipos no namespace <xref:System.Collections>, a menos que o seu foco seja especificamente o .NET Framework versão 1.1. As versões genéricas e simultâneas das coleções são as preferíveis devido à maior segurança de tipo e outras melhorias.  
  
 Considere as perguntas a seguir:  
  
-   Você precisa de uma lista sequencial em que o elemento normalmente será descartado após seu valor ser recuperado?  
  
    -   Em caso afirmativo, considere usar a classe <xref:System.Collections.Queue> ou a classe genérica <xref:System.Collections.Generic.Queue%601> caso precise do comportamento PEPS (primeiro a entrar, primeiro a sair). Considere usar a classe <xref:System.Collections.Stack> ou a classe genérica <xref:System.Collections.Generic.Stack%601> caso precise do comportamento UEPS (último a entrar, primeiro a sair). Para obter acesso seguro a partir de vários threads, use as versões simultâneas <xref:System.Collections.Concurrent.ConcurrentQueue%601> e <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
    -   Caso contrário, considere usar outras coleções.  
  
-   Você precisa acessar os elementos em uma ordem específica, como PEPS, UEPS ou aleatória?  
  
    -   A classe <xref:System.Collections.Queue> e as classes genéricas <xref:System.Collections.Generic.Queue%601> ou <xref:System.Collections.Concurrent.ConcurrentQueue%601> oferecem acesso PEPS. Para obter mais informações, consulte [Quando usar uma coleção thread-safe](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   A classe <xref:System.Collections.Stack> e as classes genéricas <xref:System.Collections.Generic.Stack%601> ou <xref:System.Collections.Concurrent.ConcurrentStack%601> oferecem acesso UEPS. Para obter mais informações, consulte [Quando usar uma coleção thread-safe](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   A classe genérica <xref:System.Collections.Generic.LinkedList%601> permite o acesso sequencial de ponta a ponta.  
  
-   Você precisa acessar cada elemento pelo índice?  
  
    -   As classes <xref:System.Collections.ArrayList> e <xref:System.Collections.Specialized.StringCollection> e a classe genérica <xref:System.Collections.Generic.List%601> oferecem acesso aos seus elementos pelo índice baseado em zero do elemento.  
  
    -   As classes <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary> e <xref:System.Collections.Specialized.StringDictionary>, e as classes genéricas <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.Generic.SortedDictionary%602>, oferecem acesso aos seus elementos pela chave do elemento.  
  
    -   As classes <xref:System.Collections.Specialized.NameObjectCollectionBase> e <xref:System.Collections.Specialized.NameValueCollection>, e as classes genéricas <xref:System.Collections.ObjectModel.KeyedCollection%602> e <xref:System.Collections.Generic.SortedList%602>, oferecem acesso aos seus elementos pelo índice baseado em zero ou pela chave do elemento.  
  
-   Cada elemento conterá um valor, uma combinação de uma chave e um valor ou uma combinação de uma chave e diversos valores?  
  
    -   Um valor: use qualquer uma das coleções baseadas na interface do <xref:System.Collections.IList> ou na interface genérica do <xref:System.Collections.Generic.IList%601>.  
  
    -   Uma chave e um valor: use qualquer uma das coleções baseadas na interface do <xref:System.Collections.IDictionary> ou na interface genérica do <xref:System.Collections.Generic.IDictionary%602>.  
  
    -   Um valor com chave incorporada: use a classe genérica <xref:System.Collections.ObjectModel.KeyedCollection%602>.  
  
    -   Uma chave e vários valores: use a classe <xref:System.Collections.Specialized.NameValueCollection>.  
  
-   Você precisa classificar os elementos de forma diferente de como foram inseridos?  
  
    -   O <xref:System.Collections.Hashtable> classifica os elementos dele pelos próprios códigos hash.  
  
    -   A classe <xref:System.Collections.SortedList> e as classes genéricas <xref:System.Collections.Generic.SortedDictionary%602> e <xref:System.Collections.Generic.SortedList%602> classificam os respectivos elementos pela chave, com base nas implementações da interface <xref:System.Collections.IComparer> e da interface genérica <xref:System.Collections.Generic.IComparer%601>.  
  
    -   O <xref:System.Collections.ArrayList> oferece um método <xref:System.Collections.ArrayList.Sort%2A> que usa uma implementação <xref:System.Collections.IComparer> como parâmetro. Seu equivalente genérico, a classe genérica <xref:System.Collections.Generic.List%601>, fornece um método <xref:System.Collections.Generic.List%601.Sort%2A> que usa uma implementação da interface genérica <xref:System.Collections.Generic.IComparer%601> como parâmetro.  
  
-   Você precisa de rapidez para pesquisas e recuperação de informações?  
  
    -   <xref:System.Collections.Specialized.ListDictionary> é mais rápido do que o <xref:System.Collections.Hashtable> para pequenas coleções (10 itens ou menos). A classe genérica <xref:System.Collections.Generic.Dictionary%602> fornece pesquisa mais rápida do que a classe genérica <xref:System.Collections.Generic.SortedDictionary%602>. A implementação com multithread é <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. O <xref:System.Collections.Concurrent.ConcurrentBag%601> fornece uma inserção com multithread rápida para dados não ordenados. Para obter mais informações sobre os dois tipos de multi-threaded, consulte [Quando usar uma coleção thread-safe](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
-   Você precisa de coleções que aceitem apenas cadeias de caracteres?  
  
    -   <xref:System.Collections.Specialized.StringCollection> (com base no <xref:System.Collections.IList>) e <xref:System.Collections.Specialized.StringDictionary> (com base no <xref:System.Collections.IDictionary>) estão no namespace <xref:System.Collections.Specialized>.  
  
    -   Além disso, é possível usar qualquer uma das classes genéricas de coleção no namespace <xref:System.Collections.Generic> como coleções de cadeias de caracteres fortemente tipadas especificando a classe <xref:System.String> para seus argumentos de tipo genérico.  
  
## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects e PLINQ  
 O LINQ to Objects permite que os desenvolvedores usem consultas LINQ para acessar objetos na memória, desde que o tipo de objeto implemente <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>. As consultas LINQ fornecem um padrão comum para acessar dados, são geralmente mais concisas e legíveis que os loops padrão `foreach` e fornecem capacidades de filtragem, ordenação e agrupamento. Para obter mais informações, consulte [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).  
  
 PLINQ fornece uma implementação paralela de LINQ to Objects que pode oferecer uma execução de consulta mais rápida em muitos cenários, por meio do uso mais eficiente dos computadores de vários núcleos. Para obter mais informações, consulte [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections>  
 <xref:System.Collections.Specialized>  
 <xref:System.Collections.Generic>  
 [Coleções Thread-Safe](../../../docs/standard/collections/thread-safe/index.md)
