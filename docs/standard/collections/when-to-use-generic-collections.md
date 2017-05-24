---
title: "Quando usar coleções genéricas | Microsoft Docs"
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
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9dcf0802b1d9a1d6b63d108289cbc814b73e8c48
ms.contentlocale: pt-br
ms.lasthandoff: 04/18/2017

---
# <a name="when-to-use-generic-collections"></a>Quando usar coleções genéricas
Geralmente é recomendável usar coleções genéricas, porque você obtém a vantagem imediata da segurança de tipos sem precisar derivar de um tipo de coleção base e implementar membros específicos do tipo. Tipos de coleção genérica também geralmente executam melhor do que os tipos de coleção não genérica correspondentes (e melhor do que tipos que são derivados de tipos de coleção base não genérica) quando os elementos da coleção forem tipos de valor, pois com genéricos não é necessário colocar os elementos em caixa.  
  
 Para programas destinados ao [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou posterior, você deve usar as classes de coleção genéricas no namespace <xref:System.Collections.Concurrent> quando vários threads possam estar adicionando ou removendo itens da coleção simultaneamente.  
  
 Os seguintes tipos genéricos correspondem aos tipos de coleção existentes:  
  
-   <xref:System.Collections.Generic.List%601> é a classe genérica que corresponde à <xref:System.Collections.ArrayList>.  
  
-   <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.Concurrent.ConcurrentDictionary%602> são as classes genéricas que correspondem à <xref:System.Collections.Hashtable>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601> é a classe genérica que corresponde à <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> pode ser usada como uma classe base, mas diferentemente de <xref:System.Collections.CollectionBase>, não é abstrata. Isso facilita muito o seu uso.  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> é a classe genérica que corresponde à <xref:System.Collections.ReadOnlyCollectionBase>. A <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> não é abstrata e tem um construtor que facilita a exposição de um <xref:System.Collections.Generic.List%601> existente como uma coleção somente leitura.  
  
-   As classes genéricas <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601> e <xref:System.Collections.Generic.SortedList%602> correspondem às respectivas classes não genéricas com os mesmos nomes.  
  
## <a name="additional-types"></a>Tipos adicionais  
 Vários tipos de coleção genérica não têm equivalentes não genéricas. Elas incluem o seguinte:  
  
-   <xref:System.Collections.Generic.LinkedList%601> é uma lista vinculada de uso geral que fornece operações de inserção e remoção de O(1).  
  
-   <xref:System.Collections.Generic.SortedDictionary%602> é um dicionário classificado com operações de inserção e recuperação de O(log `n`), representando uma alternativa útil a <xref:System.Collections.Generic.SortedList%602>.  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602> é um híbrido entre uma lista e um dicionário, que fornece uma maneira de armazenar objetos que contêm suas próprias chaves.  
  
-   <xref:System.Collections.Concurrent.BlockingCollection%601> implementa uma classe de coleção com as funcionalidades de limitação e bloqueio.  
  
-   <xref:System.Collections.Concurrent.ConcurrentBag%601> fornece inserção e remoção rápidas de elementos não ordenados.  
  
## <a name="linq-to-objects"></a>Objetos LINQ to  
 O recurso LINQ to Objects permite que você use consultas LINQ para acessar objetos na memória, desde que o tipo de objeto implemente a interface <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>. Consultas LINQ fornecem um padrão comum para acessar dados; são geralmente mais concisas e legíveis que os loops `foreach` padrão; e fornecem recursos de filtragem, classificação e agrupamento. Consultas LINQ também podem melhorar o desempenho. Para obter mais informações, consulte [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) e [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Funcionalidade adicional  
 Alguns dos tipos genéricos têm funcionalidades que não se encontram em tipos de coleção não genérica. Por exemplo, a classe <xref:System.Collections.Generic.List%601>, que corresponde à classe não genérica <xref:System.Collections.ArrayList>, tem inúmeros métodos que aceitam delegados genéricos, como o delegado <xref:System.Predicate%601> que permite especificar métodos para pesquisar a lista, o delegado <xref:System.Action%601> que representa os métodos que atuam em cada elemento da lista e o delegado <xref:System.Converter%602> que permite definir conversões entre tipos.  
  
 A classe <xref:System.Collections.Generic.List%601> permite que você especifique suas próprias implementações de interface genérica <xref:System.Collections.Generic.IComparer%601> para classificar e pesquisar a lista. As classes <xref:System.Collections.Generic.SortedDictionary%602> e <xref:System.Collections.Generic.SortedList%602> também têm essa capacidade. Além disso, essas classes permitem que você especifique comparadores quando a coleção for criada. De maneira semelhante, as classes <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.ObjectModel.KeyedCollection%602> permitem que você especifique seus próprios comparadores de igualdade.  
  
## <a name="see-also"></a>Consulte também  
 [Coleções e estruturas de dados](../../../docs/standard/collections/index.md)   
 [Tipos de coleção de uso comum](../../../docs/standard/collections/commonly-used-collection-types.md)   
 [Genéricos](../../../docs/standard/generics/index.md)
