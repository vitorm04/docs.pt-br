---
title: "Coleções genéricas no .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94da20072f793e137b0b7545c1a658ed20537a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-collections-in-the-net-framework"></a>Coleções genéricas no .NET Framework
Este tópico fornece uma visão geral das classes de coleção genérica e outros tipos genéricos no .NET Framework.  
  
## <a name="generic-collections-in-the-net-framework"></a>Coleções genéricas no .NET Framework  
 A biblioteca de classes do .NET Framework fornece um número de classes de coleção genérica de <xref:System.Collections.Generic> e <xref:System.Collections.ObjectModel> namespaces. Para obter mais informações sobre essas classes, consulte [usado comumente tipos de coleção](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Muitos dos tipos de coleção genérica são diretamente análogos aos tipos não genérica. <xref:System.Collections.Generic.Dictionary%602>é uma versão genérica do <xref:System.Collections.Hashtable>; ele usa a estrutura genérica <xref:System.Collections.Generic.KeyValuePair%602> para enumeração em vez de <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601>é uma versão genérica do <xref:System.Collections.ArrayList>. Há genérico <xref:System.Collections.Generic.Queue%601> e <xref:System.Collections.Generic.Stack%601> classes que correspondem às versões não genéricas.  
  
 Há versões genéricas e <xref:System.Collections.Generic.SortedList%602>. Ambas as versões são híbridas de um dicionário e uma lista. O <xref:System.Collections.Generic.SortedDictionary%602> classe genérica é um dicionário puro e não tem nenhum equivalente não genérico.  
  
 O <xref:System.Collections.Generic.LinkedList%601> classe genérica é uma lista vinculada true. Ele tem nenhum equivalente não genérico.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 O <xref:System.Collections.ObjectModel.Collection%601> classe genérica fornece uma classe base para derivar seus próprios tipos de coleção genérica. O <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> classe fornece uma maneira fácil de produzir uma coleção somente leitura de qualquer tipo que implementa o <xref:System.Collections.Generic.IList%601> interface genérica. O <xref:System.Collections.ObjectModel.KeyedCollection%602> classe genérica fornece uma maneira de armazenar objetos que contêm suas próprias chaves.  
  
## <a name="other-generic-types"></a>Outros tipos genéricos  
 O <xref:System.Nullable%601> estrutura genérica permite que você use tipos de valor como se eles podem ser atribuídos `null`. Isso pode ser útil ao trabalhar com consultas de banco de dados, onde os campos que contêm tipos de valor podem estar ausentes. O parâmetro de tipo genérico pode ser qualquer tipo de valor.  
  
> [!NOTE]
>  No c#, não é necessário usar <xref:System.Nullable%601> explicitamente porque a linguagem possui sintaxe para tipos anuláveis.  
  
 O <xref:System.ArraySegment%601> estrutura genérica fornece uma maneira de delimitar um intervalo de elementos dentro de uma matriz unidimensional, de qualquer tipo. O parâmetro de tipo genérico é o tipo dos elementos da matriz.  
  
 O <xref:System.EventHandler%601> delegado genérico elimina a necessidade de declarar um tipo de delegado para manipular eventos, se o evento segue o padrão de manipulação de eventos usado pelo [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Por exemplo, suponha que você tenha criado um `MyEventArgs` classe derivada de <xref:System.EventArgs>, para manter os dados para o evento. Em seguida, você pode declarar o evento da seguinte maneira:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Genéricos](../../../docs/standard/generics/index.md)  
 [Delegados genéricos para manipulação de matrizes e listas](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Interfaces genéricas](../../../docs/standard/generics/interfaces.md)
