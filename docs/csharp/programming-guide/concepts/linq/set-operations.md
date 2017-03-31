---
title: "Operações de conjunto (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 37841cde3aa5e4aaa6545b3a160422d024be5842
ms.lasthandoff: 03/13/2017

---
# <a name="set-operations-c"></a>Operações de conjunto (C#)
As operações de conjunto na LINQ referem-se a operações de consulta que geram um conjunto de resultados baseado na presença ou ausência de elementos equivalentes dentro da mesma ou de coleções (ou conjuntos) separadas.  
  
 Os métodos de operador de consulta padrão que executam operações de conjunto estão listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Remove os valores duplicados de uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName>|  
|Exceto|Retorna a diferença de conjunto, que significa os elementos de uma coleção que não aparecem em uma segunda coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=fullName>|  
|Interseção|Retorna a interseção de conjunto, o que significa os elementos que aparecem em cada uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName>|  
|União|Retorna a união de conjunto, o que significa os elementos únicos que aparecem em qualquer uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=fullName>|  
  
## <a name="comparison-of-set-operations"></a>Comparação de operações de conjuntos  
  
### <a name="distinct"></a>Distinct  
 A ilustração a seguir descreve o comportamento do método <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> em uma sequência de caracteres. A sequência retornada contém os elementos exclusivos da sequência de entrada.  
  
 ![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")  
  
### <a name="except"></a>Exceto  
 A ilustração a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>. A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.  
  
 ![Gráfico mostrando a ação de Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")  
  
### <a name="intersect"></a>Interseção  
 A ilustração a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>. A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.  
  
 ![Gráfico mostrando a interseção de duas sequências.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>União  
 A ilustração a seguir descreve uma operação de união em duas sequências de caracteres. A sequência retornada contém os elementos exclusivos das duas sequências de entrada.  
  
 ![Gráfico mostrando a união de duas sequências. ](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Como combinar e comparar coleções de cadeias de caracteres (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)   
 [Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
