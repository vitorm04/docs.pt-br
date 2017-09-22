---
title: "Tipos de coleção de uso comum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [.NET Framework], generic
- objects [.NET Framework], grouping in collections
- generics [.NET Framework], collections
- IList interface, grouping data in collections
- IDictionary interface, grouping data in collections
- grouping data in collections, generic collection types
- Collections classes
- generic collections
ms.assetid: f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55
caps.latest.revision: 29
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: b37d1d7ff75aebfcdf3e849931a5d2b3924d5d7a
ms.openlocfilehash: dfdfea20aeb8d0002ef22b9649afc09f80caeae2
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="commonly-used-collection-types"></a>Tipos de coleção de uso comum
Tipos de coleção são as variações comuns de coleções de dados, como tabelas de hash, filas, pilhas, pacotes, dicionários e listas.  
  
 Coleções são baseadas nas interfaces <xref:System.Collections.ICollection>, <xref:System.Collections.IList>, <xref:System.Collections.IDictionary> ou em seus equivalentes genéricos. As interfaces <xref:System.Collections.IList> e <xref:System.Collections.IDictionary> são ambas derivadas da interface <xref:System.Collections.ICollection>; portanto, todas as coleções são baseadas na interface <xref:System.Collections.ICollection> direta ou indiretamente. Em coleções baseadas na interface <xref:System.Collections.IList> (tal como, <xref:System.Array>, <xref:System.Collections.ArrayList> ou <xref:System.Collections.Generic.List%601>) ou diretamente na interface <xref:System.Collections.ICollection> (tal como, <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> ou <xref:System.Collections.Generic.LinkedList%601>), cada elemento contém apenas um valor. Em coleções baseadas na interface <xref:System.Collections.IDictionary> (tal como as classes <xref:System.Collections.Hashtable> e <xref:System.Collections.SortedList>, as classes genéricas <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.Generic.SortedList%602>) ou as classes <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, cada elemento contém uma chave e um valor.  A classe <xref:System.Collections.ObjectModel.KeyedCollection%602> é exclusiva, pois ela é uma lista de valores com chaves incorporadas aos valores e portanto se comporta como uma lista e como um dicionário.  
  
 Coleções genéricas são a melhor solução para tipagem forte. No entanto, se o idioma não oferecer suporte a genéricos, o namespace <xref:System.Collections> incluirá coleções base, tais como <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase> e <xref:System.Collections.DictionaryBase>, que são classes base abstratas que podem ser estendidas para criar classes de coleção que são fortemente tipadas. Quando for necessário acesso de coleção com multithread eficiente, use as coleções genéricas no namespace <xref:System.Collections.Concurrent>.  
  
 As coleções podem variar, dependendo de como os elementos são armazenados, como são classificados, como as pesquisas são executadas e como são feitas comparações. A classe <xref:System.Collections.Queue> e a classe genérica <xref:System.Collections.Generic.Queue%601> fornecem listas primeiro a entrar, primeiro a sair, enquanto a classe <xref:System.Collections.Stack> e a classe genérica <xref:System.Collections.Generic.Stack%601> fornecem listas último a entrar, primeiro a sair. A classe <xref:System.Collections.SortedList> e a classe genérica <xref:System.Collections.Generic.SortedList%602> fornecem versões classificadas da classe <xref:System.Collections.Hashtable> e da classe genérica <xref:System.Collections.Generic.Dictionary%602>. Os elementos de uma <xref:System.Collections.Hashtable> ou uma <xref:System.Collections.Generic.Dictionary%602> são acessíveis somente pela chave do elemento, mas os elementos de uma <xref:System.Collections.SortedList> ou uma <xref:System.Collections.ObjectModel.KeyedCollection%602> são acessíveis pela chave ou pelo índice do elemento. Os índices em todas as coleções são baseados em zero, exceto <xref:System.Array>, que permite matrizes que não sejam baseadas em zero.  
  
 O recurso LINQ para objetos permite que você use consultas LINQ para acessar objetos na memória, desde que o tipo de objeto implemente <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>. Consultas LINQ fornecem um padrão comum para acessar dados; são geralmente mais concisas e legíveis que os loops `foreach` padrão; e fornecem recursos de filtragem, classificação e agrupamento. Consultas LINQ também podem melhorar o desempenho. Para obter mais informações, consulte [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) e [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Coleções e Estruturas de Dados](../../../docs/standard/collections/index.md)|Discute os diversos tipos de coleção disponíveis no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], incluindo pilhas, filas, listas, matrizes e dicionários.|  
|[Tipos de Coleção de Tabela de Hash e Dicionário](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Descreve os recursos de tipos de dicionário baseados em hash genérico e não genérico.|  
|[Tipos de Coleção Sorted](../../../docs/standard/collections/sorted-collection-types.md)|Descreve as classes que fornecem funcionalidade de classificação para listas e conjuntos.|  
|[Genéricos](../../../docs/standard/generics/index.md)|Descreve o recurso Genéricos, incluindo coleções, delegados e interfaces genéricos fornecidos pelo [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Fornece links à documentação de recursos para C#, Visual Basic e Visual C++ e para oferecer suporte a tecnologias, tais como a de reflexão.|  
  
## <a name="reference"></a>Referência  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>

