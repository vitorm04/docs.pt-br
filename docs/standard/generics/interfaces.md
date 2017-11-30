---
title: "Interfaces genéricas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generic interfaces [.NET Framework]
- equality comparisons [.NET Framework]
- generics [.NET Framework], interfaces
- ordering comparisons [.NET Framework]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71cc1410a13fc73cce931a063a929ba94aab91be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-interfaces"></a>Interfaces genéricas
Este tópico fornece uma visão geral das interfaces genéricas que fornecem a funcionalidade comum entre famílias de tipos genéricos.  
  
## <a name="generic-interfaces"></a>Interfaces genéricas  
 Interfaces genéricas fornecem contrapartes de tipo seguro para interfaces não genéricas para comparações de ordenação e de igualdade e para a funcionalidade que é compartilhada por tipos de coleção genérica.  
  
> [!NOTE]
>  Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], os parâmetros de tipo de várias interfaces genéricas são marcados covariantes ou contravariant, fornecendo maior flexibilidade na atribuição e usando tipos que implementam essas interfaces. Consulte [Covariância e contravariância](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Igualdade e comparações de ordenação  
 No <xref:System> namespace, o <xref:System.IComparable%601?displayProperty=nameWithType> e <xref:System.IEquatable%601?displayProperty=nameWithType> interfaces genéricas, como suas contrapartes não genéricas, definem métodos de comparações de classificação e comparações de igualdade, respectivamente. Tipos implementam essas interfaces para fornecer a capacidade de executar tais comparações.  
  
 No <xref:System.Collections.Generic> namespace, o <xref:System.Collections.Generic.IComparer%601> e <xref:System.Collections.Generic.IEqualityComparer%601> interfaces genéricas oferecem uma maneira de definir uma comparação de classificação ou de igualdade para tipos que não implementam a <xref:System.IComparable%601?displayProperty=nameWithType> ou <xref:System.IEquatable%601?displayProperty=nameWithType> interface genérica e eles fornecem uma maneira de Redefina esses relacionamentos para tipos que implementam. Essas interfaces são usadas pelos métodos e construtores de muitas das classes de coleção genérica. Por exemplo, você pode passar um genérico <xref:System.Collections.Generic.IComparer%601> objeto para o construtor do <xref:System.Collections.Generic.SortedDictionary%602> classe para especificar uma ordem de classificação para um tipo que não implementa um genérico <xref:System.IComparable%601?displayProperty=nameWithType>. Há sobrecargas do <xref:System.Array.Sort%2A?displayProperty=nameWithType> método estático genérico e o <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> método de instância para classificar matrizes e listas usando genérico <xref:System.Collections.Generic.IComparer%601> implementações.  
  
 O <xref:System.Collections.Generic.Comparer%601> e <xref:System.Collections.Generic.EqualityComparer%601> classes genéricas fornecem classes base para implementações do <xref:System.Collections.Generic.IComparer%601> e <xref:System.Collections.Generic.IEqualityComparer%601> interfaces genéricas e também fornecem padrão de comparações de ordenação e de igualdade por meio de suas respectivas <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> e <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> propriedades.  
  
### <a name="collection-functionality"></a>Funcionalidade de coleta  
 O <xref:System.Collections.Generic.ICollection%601> interface genérica é a interface básica para tipos de coleção genérica. Ele fornece a funcionalidade básica para adicionar, remover, copiar e enumerar elementos. <xref:System.Collections.Generic.ICollection%601>herda tanto do genérico <xref:System.Collections.Generic.IEnumerable%601> genéricas e <xref:System.Collections.IEnumerable>.  
  
 O <xref:System.Collections.Generic.IList%601> interface genérica estende o <xref:System.Collections.Generic.ICollection%601> interface genérica com métodos para recuperação indexada.  
  
 O <xref:System.Collections.Generic.IDictionary%602> interface genérica estende o <xref:System.Collections.Generic.ICollection%601> interface genérica com métodos para recuperação por chave. Tipos de dicionário genérico na biblioteca de classe base do .NET Framework também implementam não genérica <xref:System.Collections.IDictionary> interface.  
  
 O <xref:System.Collections.Generic.IEnumerable%601> interface genérica fornece uma estrutura de enumerador genérico. O <xref:System.Collections.Generic.IEnumerator%601> interface genérica implementada pelo enumeradores genéricos herda não genérica <xref:System.Collections.IEnumerator> interface; o <xref:System.Collections.IEnumerator.MoveNext%2A> e <xref:System.Collections.IEnumerator.Reset%2A> membros, que não dependem do parâmetro de tipo `T`, só aparecem nos não genérica interface. Isso significa que qualquer consumidor da interface não genérica também pode consumir a interface genérica.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Genéricos](../../../docs/standard/generics/index.md)  
 [Coleções genéricas no .NET Framework](../../../docs/standard/generics/collections.md)  
 [Delegados genéricos para manipulação de matrizes e listas](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Covariância e Contravariância](../../../docs/standard/generics/covariance-and-contravariance.md)
