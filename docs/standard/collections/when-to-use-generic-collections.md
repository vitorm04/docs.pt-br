---
title: Quando usar coleções genéricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9831212cf65e3913bae2431e4746b5def03430b6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703669"
---
# <a name="when-to-use-generic-collections"></a>Quando usar coleções genéricas
Geralmente é recomendável usar coleções genéricas, porque você obtém a vantagem imediata da segurança de tipos sem precisar derivar de um tipo de coleção base e implementar membros específicos do tipo. Tipos de coleção genérica também geralmente executam melhor do que os tipos de coleção não genérica correspondentes (e melhor do que tipos que são derivados de tipos de coleção base não genérica) quando os elementos da coleção forem tipos de valor, pois com genéricos não é necessário colocar os elementos em caixa.  
  
 Para programas destinados à [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou posterior, você deve usar as classes de coleção genérica no namespace <xref:System.Collections.Concurrent> quando vários threads puderem adicionar ou remover itens da coleção simultaneamente.  
  
 Os seguintes tipos genéricos correspondem aos tipos de coleção existentes:  
  
-   <xref:System.Collections.Generic.List%601> é a classe genérica que corresponde à <xref:System.Collections.ArrayList>.  
  
-   <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.Concurrent.ConcurrentDictionary%602> são as classes genéricas que correspondem à <xref:System.Collections.Hashtable>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601> é a classe genérica que corresponde à <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> pode ser usada como uma classe base, mas ao contrário de <xref:System.Collections.CollectionBase>, ela não é abstrata. Isso facilita muito o seu uso.  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> é a classe genérica que corresponde à <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> não é abstrata e tem um construtor que facilita expor uma <xref:System.Collections.Generic.List%601> existente como uma coleção somente leitura.  
  
-   As classes genéricas <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601> e <xref:System.Collections.Generic.SortedList%602> correspondem às classes não genéricas respectivas com os mesmos nomes.  
  
## <a name="additional-types"></a>Tipos adicionais  
 Vários tipos de coleção genérica não têm equivalentes não genéricas. Elas incluem o seguinte:  
  
-   <xref:System.Collections.Generic.LinkedList%601> é uma lista vinculada de uso geral que fornece operações de inserção e remoção O(1).  
  
-   <xref:System.Collections.Generic.SortedDictionary%602> é um dicionário classificado com operações de inserção e recuperação O(log `n`), o que o torna uma alternativa útil para <xref:System.Collections.Generic.SortedList%602>.  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602> é um híbrido entre uma lista e um dicionário, que fornece uma maneira de armazenar objetos que contenham suas próprias chaves.  
  
-   <xref:System.Collections.Concurrent.BlockingCollection%601> implementa uma classe de coleção com funcionalidade de delimitação e bloqueio.  
  
-   <xref:System.Collections.Concurrent.ConcurrentBag%601> fornece rápida inserção e remoção de elementos não classificados.  
  
## <a name="linq-to-objects"></a>Objetos LINQ to  
 O recurso LINQ para objetos permite que você use consultas LINQ para acessar objetos na memória, desde que o tipo de objeto implemente a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Consultas LINQ fornecem um padrão comum para acessar dados; são geralmente mais concisas e legíveis que os loops `foreach` padrão; e fornecem recursos de filtragem, classificação e agrupamento. Consultas LINQ também podem melhorar o desempenho. Para obter mais informações, consulte [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) e [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Funcionalidade adicional  
 Alguns dos tipos genéricos possuem funcionalidades que não se encontram em tipos de coleção genérica. Por exemplo, a classe <xref:System.Collections.Generic.List%601>, que corresponde à classe <xref:System.Collections.ArrayList> não genérica, possui vários métodos que aceitam delegados genéricos, tais como o delegado <xref:System.Predicate%601> que permite que você especifique métodos para pesquisa na lista, o delegado <xref:System.Action%601> que representa métodos que atuam em cada elemento da lista e o delegado <xref:System.Converter%602> que permite definir conversões entre tipos.  
  
 A classe <xref:System.Collections.Generic.List%601> permite que você especifique suas próprias implementações de interface genérica <xref:System.Collections.Generic.IComparer%601> para classificação e pesquisa na lista. As classes <xref:System.Collections.Generic.SortedDictionary%602> e <xref:System.Collections.Generic.SortedList%602> também possuem esse recurso. Além disso, essas classes permitem que você especifique comparadores quando a coleção for criada. De maneira semelhante, as classes <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.ObjectModel.KeyedCollection%602> permitem que você especifique seus próprios comparadores de igualdade.  
  
## <a name="see-also"></a>Consulte também

- [Coleções e Estruturas de Dados](../../../docs/standard/collections/index.md)  
- [Tipos de Coleção de Uso Comum](../../../docs/standard/collections/commonly-used-collection-types.md)  
- [Genéricos](../../../docs/standard/generics/index.md)
