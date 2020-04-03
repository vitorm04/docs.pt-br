---
title: Quando usar coleções genéricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: bbf8ec7f61981332b6984488b369fee62959b92a
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635896"
---
# <a name="when-to-use-generic-collections"></a>Quando usar coleções genéricas

O uso de coleções genéricas dá-lhe o benefício automático da segurança do tipo sem ter que derivar de um tipo de coleta base e implementar membros específicos do tipo. Os tipos de coleta genéricas também geralmente têm um desempenho melhor do que os tipos de coleta não genéricos correspondentes (e melhores do que os tipos que são derivados de tipos de coleta de base não genéricos) quando os elementos de coleta são tipos de valor, porque com genéricos, não há necessidade de encaixotar os elementos.  
  
 Para programas direcionados ao .NET Framework 4 ou posterior, você deve usar as classes de coleção genérica no namespace <xref:System.Collections.Concurrent> quando vários threads puderem adicionar ou remover itens da coleção simultaneamente.  
  
 Os seguintes tipos genéricos correspondem aos tipos de coleção existentes:  
  
- <xref:System.Collections.Generic.List%601> é a classe genérica que corresponde à <xref:System.Collections.ArrayList>.  
  
- <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.Concurrent.ConcurrentDictionary%602> são as classes genéricas que correspondem à <xref:System.Collections.Hashtable>.  
  
- <xref:System.Collections.ObjectModel.Collection%601> é a classe genérica que corresponde à <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601>pode ser usado como uma <xref:System.Collections.CollectionBase>classe base, mas ao contrário, não é abstrato, o que torna muito mais fácil de usar.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> é a classe genérica que corresponde à <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> não é abstrata e tem um construtor que facilita expor uma <xref:System.Collections.Generic.List%601> existente como uma coleção somente leitura.  
  
- As classes genéricas <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601> e <xref:System.Collections.Generic.SortedList%602> correspondem às classes não genéricas respectivas com os mesmos nomes.  
  
## <a name="additional-types"></a>Tipos adicionais  
 Vários tipos de coleção genérica não têm equivalentes não genéricas. São elas:  
  
- <xref:System.Collections.Generic.LinkedList%601> é uma lista vinculada de uso geral que fornece operações de inserção e remoção O(1).  
  
- <xref:System.Collections.Generic.SortedDictionary%602> é um dicionário classificado com operações de inserção e recuperação O(log `n`), o que o torna uma alternativa útil para <xref:System.Collections.Generic.SortedList%602>.  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602> é um híbrido entre uma lista e um dicionário, que fornece uma maneira de armazenar objetos que contenham suas próprias chaves.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601> implementa uma classe de coleção com funcionalidade de delimitação e bloqueio.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601> fornece rápida inserção e remoção de elementos não classificados.  
  
## <a name="linq-to-objects"></a>Objetos LINQ to  
 O recurso LINQ para objetos permite que você use consultas LINQ para acessar objetos na memória, desde que o tipo de objeto implemente a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. As consultas LINQ fornecem um padrão comum para acessar dados; são tipicamente mais concisos `foreach` e legíveis do que os loops padrão; e fornecer recursos de filtragem, encomenda e agrupamento. Consultas LINQ também podem melhorar o desempenho. Para obter mais informações, confira [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) e [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).  
  
## <a name="additional-functionality"></a>Funcionalidade adicional  
 Alguns dos tipos genéricos possuem funcionalidades que não se encontram em tipos de coleção genérica. Por exemplo, a classe <xref:System.Collections.Generic.List%601>, que corresponde à classe <xref:System.Collections.ArrayList> não genérica, possui vários métodos que aceitam delegados genéricos, tais como o delegado <xref:System.Predicate%601> que permite que você especifique métodos para pesquisa na lista, o delegado <xref:System.Action%601> que representa métodos que atuam em cada elemento da lista e o delegado <xref:System.Converter%602> que permite definir conversões entre tipos.  
  
 A classe <xref:System.Collections.Generic.List%601> permite que você especifique suas próprias implementações de interface genérica <xref:System.Collections.Generic.IComparer%601> para classificação e pesquisa na lista. As classes <xref:System.Collections.Generic.SortedDictionary%602> e <xref:System.Collections.Generic.SortedList%602> também possuem esse recurso. Além disso, essas classes permitem que você especifique comparadores quando a coleção for criada. De maneira semelhante, as classes <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.ObjectModel.KeyedCollection%602> permitem que você especifique seus próprios comparadores de igualdade.  
  
## <a name="see-also"></a>Confira também

- [Coleções e Estruturas de Dados](../../../docs/standard/collections/index.md)
- [Tipos de coleção de uso comum](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Genéricos](../../../docs/standard/generics/index.md)
