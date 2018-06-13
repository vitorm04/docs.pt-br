---
title: Operações de conjunto (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 45b828f89b380b2649ab5ee80f5438d822de9443
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334406"
---
# <a name="set-operations-c"></a>Operações de conjunto (C#)
As operações de conjunto na LINQ referem-se a operações de consulta que geram um conjunto de resultados baseado na presença ou ausência de elementos equivalentes dentro da mesma ou de coleções (ou conjuntos) separadas.  
  
 Os métodos de operador de consulta padrão que executam operações de conjunto estão listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Remove os valores duplicados de uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Exceto|Retorna a diferença de conjunto, que significa os elementos de uma coleção que não aparecem em uma segunda coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Interseção|Retorna a interseção de conjunto, o que significa os elementos que aparecem em cada uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|União|Retorna a união de conjunto, o que significa os elementos únicos que aparecem em qualquer uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Comparação de operações de conjuntos  
  
### <a name="distinct"></a>Distinct  
 A ilustração a seguir mostra o comportamento do método <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> em uma sequência de caracteres. A sequência retornada contém os elementos exclusivos da sequência de entrada.  
  
 ![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")  
  
### <a name="except"></a>Exceto  
 A ilustração a seguir mostra o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.  
  
 ![Gráfico mostrando a ação de Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")  
  
### <a name="intersect"></a>Interseção  
 A ilustração a seguir mostra o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.  
  
 ![Gráfico mostrando a interseção de duas sequências.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>União  
 A ilustração a seguir descreve uma operação de união em duas sequências de caracteres. A sequência retornada contém os elementos exclusivos das duas sequências de entrada.  
  
 ![Gráfico mostrando a união de duas sequências. ](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>  
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Como combinar e comparar coleções de cadeias de caracteres (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
