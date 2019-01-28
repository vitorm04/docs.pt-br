---
title: Coleções genéricas no .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec3f8fb16245318cab8706a2ed136e51f3dc31db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705791"
---
# <a name="generic-collections-in-net"></a>Coleções genéricas no .NET

 A biblioteca de classes do .NET fornece várias classes de coleção genérica nos namespaces <xref:System.Collections.Generic> e <xref:System.Collections.ObjectModel>. Para obter informações detalhadas sobre essas classes, consulte [Tipos de coleção comumente usados](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Muitos dos tipos de coleção genéricos são diretamente análogos aos tipos não genéricos. <xref:System.Collections.Generic.Dictionary%602> é uma versão genérica de <xref:System.Collections.Hashtable>; ele usa a estrutura genérica <xref:System.Collections.Generic.KeyValuePair%602> para enumeração em vez de <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> é uma versão genérica de <xref:System.Collections.ArrayList>. Há classes <xref:System.Collections.Generic.Queue%601> e <xref:System.Collections.Generic.Stack%601> genéricas que correspondem às versões não genéricas.  
  
 Há versões genéricas e não genéricas de <xref:System.Collections.Generic.SortedList%602>. As duas versões são híbridas de um dicionário e de uma lista. A classe genérica <xref:System.Collections.Generic.SortedDictionary%602> é um dicionário puro e não tem nenhum equivalente não genérico.  
  
 A classe genérica <xref:System.Collections.Generic.LinkedList%601> é uma verdadeira lista vinculada. Não tem nenhum equivalente não genérico.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 A classe genérica <xref:System.Collections.ObjectModel.Collection%601> fornece uma classe base para derivar seus próprios tipos de coleção genérica. A classe <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> fornece uma maneira fácil de produzir uma coleção somente leitura de qualquer tipo que implementa a interface genérica <xref:System.Collections.Generic.IList%601>. A classe genérica <xref:System.Collections.ObjectModel.KeyedCollection%602> fornece uma maneira de armazenar objetos que contêm suas próprias chaves.  
  
## <a name="other-generic-types"></a>Outros tipos genéricos  
 A estrutura genérica <xref:System.Nullable%601> permite que você use tipos de valor como se eles pudessem ser atribuídos `null`. Isso pode ser útil ao trabalhar com consultas de banco de dados, nas quais os campos que contêm tipos de valor podem estar ausentes. O parâmetro de tipo genérico pode ser qualquer tipo de valor.  
  
> [!NOTE]
>  No C# e Visual Basic não é necessário usar <xref:System.Nullable%601> explicitamente, pois a linguagem tem sintaxe para tipos que permitem valor nulo. Consulte [Tipos que permitem valor nulo (Guia de programação em C#)](../../csharp/programming-guide/nullable-types/index.md) e [Tipos de valor que permitem valor nulo (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 A estrutura genérica <xref:System.ArraySegment%601> fornece uma maneira de delimitar um intervalo de elementos dentro de uma matriz unidimensional baseada em zero de qualquer tipo. O parâmetro de tipo genérico é o tipo dos elementos da matriz.  
  
 O delegado genérico <xref:System.EventHandler%601> elimina a necessidade de declarar um tipo de delegado para manipular eventos, se o evento seguir o padrão de manipulação de eventos usado por [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Por exemplo, vamos supor que você tenha criado uma classe `MyEventArgs`, derivada de <xref:System.EventArgs>, para manter os dados para o evento. Em seguida, você pode declarar o evento da seguinte maneira:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genéricos](../../../docs/standard/generics/index.md)
- [Delegados genéricos para manipulação de matrizes e listas](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Interfaces genéricas](../../../docs/standard/generics/interfaces.md)
