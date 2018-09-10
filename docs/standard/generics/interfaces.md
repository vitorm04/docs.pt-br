---
title: Interfaces genéricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- generic interfaces [.NET Framework]
- equality comparisons [.NET Framework]
- generics [.NET Framework], interfaces
- ordering comparisons [.NET Framework]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6c151798c807206cc7f4b2fbeb21e75e9142379
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198472"
---
# <a name="generic-interfaces"></a>Interfaces genéricas
Este tópico fornece uma visão geral de interfaces genéricas que fornecem funcionalidade comum entre famílias de tipos genéricos.  
  
## <a name="generic-interfaces"></a>Interfaces genéricas  
 As interfaces genéricas fornecem contrapartes fortemente tipadas para interfaces não genéricas para fins de comparações de ordenação e de igualdade, e para a funcionalidade que é compartilhada por tipos de coleção genérica.  
  
> [!NOTE]
>  A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], os parâmetros de tipo de várias interfaces genéricas são marcados como covariantes ou contravariantes, fornecendo mais flexibilidade na atribuição e usando tipos que implementam essas interfaces. Consulte [Covariância e contravariância](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Comparações de ordem e igualdade  
 No namespace <xref:System>, as interfaces genéricas <xref:System.IComparable%601?displayProperty=nameWithType> e <xref:System.IEquatable%601?displayProperty=nameWithType>, assim como suas contrapartes não genéricas, definem métodos para comparações de classificação e de igualdade, respectivamente. Os tipos implementam essas interfaces para permitir a execução dessas comparações.  
  
 No namespace <xref:System.Collections.Generic>, as interfaces genéricas <xref:System.Collections.Generic.IComparer%601> e <xref:System.Collections.Generic.IEqualityComparer%601> oferecem uma maneira de definir uma comparação de classificação ou de igualdade para tipos que não implementam a interface genérica <xref:System.IComparable%601?displayProperty=nameWithType> ou <xref:System.IEquatable%601?displayProperty=nameWithType>, e fornecem uma maneira de redefinir esses relacionamentos para tipos que implementam. Essas interfaces são usadas pelos métodos e construtores de muitas classes de coleção genérica. Por exemplo, você pode passar um objeto <xref:System.Collections.Generic.IComparer%601> genérico para o construtor da classe <xref:System.Collections.Generic.SortedDictionary%602>, a fim de especificar uma ordem de classificação para um tipo que não implementa um <xref:System.IComparable%601?displayProperty=nameWithType> genérico. Há sobrecargas do método estático genérico <xref:System.Array.Sort%2A?displayProperty=nameWithType> e do método de instância <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> para classificar matrizes e listas usando implementações <xref:System.Collections.Generic.IComparer%601> genéricas.  
  
 As classes genéricas <xref:System.Collections.Generic.Comparer%601> e <xref:System.Collections.Generic.EqualityComparer%601> fornecem classes base para implementações das interfaces genéricas <xref:System.Collections.Generic.IComparer%601> e <xref:System.Collections.Generic.IEqualityComparer%601>, e também fornecem comparações padrão de ordem e de igualdade por meio de suas respectivas propriedades <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> e <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType>.  
  
### <a name="collection-functionality"></a>Funcionalidade de coleção  
 A interface genérica <xref:System.Collections.Generic.ICollection%601> é a interface básica para tipos de coleção genérica. Ela fornece a funcionalidade básica para adicionar, remover, copiar e enumerar elementos. <xref:System.Collections.Generic.ICollection%601> herda da <xref:System.Collections.Generic.IEnumerable%601> genérica e da <xref:System.Collections.IEnumerable> não genérica.  
  
 A interface genérica <xref:System.Collections.Generic.IList%601> estende a interface genérica <xref:System.Collections.Generic.ICollection%601> com métodos para recuperação indexada.  
  
 A interface genérica <xref:System.Collections.Generic.IDictionary%602> estende a interface genérica <xref:System.Collections.Generic.ICollection%601> com métodos para recuperação codificada. Os tipos de dicionário genérico na biblioteca de classe base do .NET Framework também implementam a interface não genérica <xref:System.Collections.IDictionary>.  
  
 A interface genérica <xref:System.Collections.Generic.IEnumerable%601> fornece uma estrutura de enumerador genérico. A interface genérica <xref:System.Collections.Generic.IEnumerator%601> implementada pelos enumeradores genéricos herda a interface não genérica <xref:System.Collections.IEnumerator>; os membros <xref:System.Collections.IEnumerator.MoveNext%2A> e <xref:System.Collections.IEnumerator.Reset%2A>, que não dependem do parâmetro de tipo `T`, só aparecem na interface não genérica. Isso significa que qualquer consumidor da interface não genérica também poderá consumir a interface genérica.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [Genéricos](../../../docs/standard/generics/index.md)  
- [Coleções genéricas no .NET Framework](../../../docs/standard/generics/collections.md)  
- [Delegados genéricos para manipulação de matrizes e listas](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
- [Covariância e Contravariância](../../../docs/standard/generics/covariance-and-contravariance.md)
