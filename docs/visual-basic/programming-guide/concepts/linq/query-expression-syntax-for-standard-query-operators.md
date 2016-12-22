---
title: "Sintaxe de express&#227;o de consulta para operadores de consulta padr&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sintaxe de express&#227;o de consulta para operadores de consulta padr&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Alguns dos operadores de consulta padrão usados com mais freqüência dedicou sintaxe palavra\-chave da linguagem Visual Basic que permite a ser chamado como parte de um *expressão de consulta*. Uma expressão de consulta é uma forma diferente e mais legível de expressar uma consulta que seu *baseada em método*  equivalente. Cláusulas de expressão de consulta são traduzidas em chamadas para os métodos de consulta em tempo de compilação.  
  
## Tabela de sintaxe de expressão de consulta  
 A tabela a seguir lista os operadores de consulta padrão que têm cláusulas de expressão de consulta equivalente.  
  
|Método|Sintaxe de expressão de consulta do Visual Basic|  
|------------|------------------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br /> \(Para obter mais informações, consulte [Cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md).\)|  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br /> \(Para obter mais informações, consulte [Cláusula Distinct](../../../../visual-basic/language-reference/queries/distinct-clause.md).\)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br /> \(Para obter mais informações, consulte [Cláusula Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md).\)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br /> \(Para obter mais informações, consulte [Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md).\)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> \- ou \-<br /><br /> `Join … [As …]In … On …`<br /><br /> \(Para obter mais informações, consulte [Cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md).\)|  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br /> \(Para obter mais informações, consulte [Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).\)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br /> \(Para obter mais informações, consulte [Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).\)|  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br /> \(Para obter mais informações, consulte [Cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).\)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Vários `From` cláusulas<br /><br /> \(Para obter mais informações, consulte [Cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md).\)|  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br /> \(Para obter mais informações, consulte [Cláusula Skip](../../../../visual-basic/language-reference/queries/skip-clause.md).\)|  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br /> \(Para obter mais informações, consulte [Ignorar cláusula While](../../../../visual-basic/language-reference/queries/skip-while-clause.md).\)|  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br /> \(Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).\)|  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br /> \(Para obter mais informações, consulte [Cláusula Take](../../../../visual-basic/language-reference/queries/take-clause.md).\)|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br /> \(Para obter mais informações, consulte [Cláusula Take While](../../../../visual-basic/language-reference/queries/take-while-clause.md).\)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br /> \(Para obter mais informações, consulte [Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).\)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br /> \(Para obter mais informações, consulte [Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).\)|  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br /> \(Para obter mais informações, consulte [Cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).\)|  
  
## Consulte também  
 <xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable>   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Classificação de operadores de consulta padrão por meio da execução \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)