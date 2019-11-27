---
title: Sintaxe de expressão da consulta para operadores de consulta padrão
ms.date: 07/20/2015
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
ms.openlocfilehash: f0c8438c8d092cbf4f1cdb8e3adba7bd9d939c32
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346546"
---
# <a name="query-expression-syntax-for-standard-query-operators-visual-basic"></a>Sintaxe de expressão de consulta para operadores de consulta padrão (Visual Basic)
Alguns dos operadores de consulta padrão usados com mais frequência têm uma sintaxe de palavra-chave de linguagem Visual Basic dedicada que permite que eles sejam chamados como parte de uma *expressão de consulta*. Uma expressão de consulta é uma maneira diferente e mais legível de expressar uma consulta do que seu equivalente *baseado em método*. As cláusulas de expressão de consulta são convertidas em chamadas para os métodos de consulta em tempo de compilação.  
  
## <a name="query-expression-syntax-table"></a>Tabela de sintaxe de expressão de consulta  
 A tabela a seguir lista os operadores de consulta padrão que têm cláusulas de expressão de consulta equivalentes.  
  
|Método|Visual Basic sintaxe de expressão de consulta|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br /> (Para obter mais informações, consulte a [cláusula from](../../../../visual-basic/language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br /> (Para obter mais informações, consulte a [cláusula DISTINCT](../../../../visual-basic/language-reference/queries/distinct-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br /> (Para obter mais informações, consulte [a cláusula Group by](../../../../visual-basic/language-reference/queries/group-by-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br /> (Para obter mais informações, consulte [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> - ou -<br /><br /> `Join … [As …]In … On …`<br /><br /> (Para obter mais informações, consulte a [cláusula JOIN](../../../../visual-basic/language-reference/queries/join-clause.md).)|  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br /> (Para obter mais informações, consulte [a cláusula order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br /> (Para obter mais informações, consulte [a cláusula order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br /> (Para obter mais informações, consulte [cláusula SELECT](../../../../visual-basic/language-reference/queries/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Várias cláusulas `From`<br /><br /> (Para obter mais informações, consulte a [cláusula from](../../../../visual-basic/language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br /> (Para obter mais informações, consulte a [cláusula Skip](../../../../visual-basic/language-reference/queries/skip-clause.md).)|  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br /> (Para obter mais informações, consulte [ignorar cláusula while](../../../../visual-basic/language-reference/queries/skip-while-clause.md).)|  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br /> (Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br /> (Para obter mais informações, consulte [cláusula Take](../../../../visual-basic/language-reference/queries/take-clause.md).)|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br /> (Para obter mais informações, veja [cláusula Take While](../../../../visual-basic/language-reference/queries/take-while-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br /> (Para obter mais informações, consulte [a cláusula order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br /> (Para obter mais informações, consulte [a cláusula order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br /> (Para obter mais informações, consulte a [cláusula WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).)|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Classificação de operadores de consulta padrão por meio de execução (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
