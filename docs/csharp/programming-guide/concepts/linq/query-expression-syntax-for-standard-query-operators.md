---
title: "Sintaxe de express&#227;o de consulta para operadores de consulta padr&#227;o (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Sintaxe de express&#227;o de consulta para operadores de consulta padr&#227;o (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Alguns dos operadores de consulta padrão usados com mais freqüência dedicou c\# sintaxe palavra\-chave da linguagem que permita a ser chamado como parte de um *expressão de consulta*. Uma expressão de consulta é uma forma diferente e mais legível de expressar uma consulta que seu *baseada em método*  equivalente. Cláusulas de expressão de consulta são traduzidas em chamadas para os métodos de consulta em tempo de compilação.  
  
## Tabela de sintaxe de expressão de consulta  
 A tabela a seguir lista os operadores de consulta padrão que têm cláusulas de expressão de consulta equivalente.  
  
|Método|Sintaxe de expressão de consulta c\#|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Use uma variável de intervalo digitadas explicitamente, por exemplo:<br /><br /> `from int i in numbers`<br /><br /> \(Para obter mais informações, consulte [Cláusula from](../../../../visual-basic/language-reference/queries/from-clause.md).\)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> \- ou \-<br /><br /> `group … by … into …`<br /><br /> \(Para obter mais informações, consulte [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md).\)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> \(Para obter mais informações, consulte [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md).\)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> \(Para obter mais informações, consulte [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md).\)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> \(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).\)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> \(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).\)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> \(Para obter mais informações, consulte [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md).\)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Vários `from` cláusulas.<br /><br /> \(Para obter mais informações, consulte [Cláusula from](../../../../visual-basic/language-reference/queries/from-clause.md).\)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> \(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).\)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> \(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).\)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> \(Para obter mais informações, consulte [Cláusula where](../../../../visual-basic/language-reference/queries/where-clause.md).\)|  
  
## Consulte também  
 <xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Classificação de operadores de consulta padrão por meio da execução \(c\#\)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)