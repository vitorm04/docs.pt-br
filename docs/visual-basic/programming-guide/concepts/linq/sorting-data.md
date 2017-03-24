---
title: Classificando dados (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d6a009573f9ff3eba71875945128ee6cd37ac37b
ms.lasthandoff: 03/13/2017

---
# <a name="sorting-data-visual-basic"></a>Classificando dados (Visual Basic)
Uma operação de classificação ordena os elementos de uma sequência com base em um ou mais atributos. O primeiro critério de classificação executa uma classificação primária nos elementos. Especificando um segundo critério de classificação, você pode classificar os elementos dentro de cada grupo de classificação principal.  
  
 A ilustração a seguir mostra os resultados de uma operação de classificação alfabética em uma sequência de caracteres.  
  
 ![Operação de classificação de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Os métodos de operador de consulta padrão que classificam dados são listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OrderBy|Classifica valores em ordem crescente.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName>|  
|OrderByDescending|Classifica valores em ordem decrescente.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName>|  
|ThenBy|Executa uma classificação secundária em ordem crescente.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName>|  
|ThenByDescending|Executa uma classificação secundária em ordem decrescente.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName>|  
|Inverso|Inverte a ordem dos elementos em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
  
### <a name="primary-sort-examples"></a>Exemplos de classificação principal  
  
#### <a name="primary-ascending-sort"></a>Classificação crescente primária  
 O exemplo a seguir demonstra como usar o `Order By` cláusula em uma consulta LINQ para classificar as cadeias de caracteres em uma matriz de comprimento de cadeia de caracteres, em ordem crescente.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a>Classificação decrescente primária  
 O exemplo a seguir demonstra como usar o `Order By Descending` cláusula em uma consulta LINQ para classificar as cadeias de caracteres pela sua primeira letra, em ordem decrescente.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a>Exemplos de classificação secundária  
  
#### <a name="secondary-ascending-sort"></a>Classificação crescente secundária  
 O exemplo a seguir demonstra como usar o `Order By` cláusula em uma consulta LINQ para executar uma classificação primária e secundária das cadeias de caracteres em uma matriz. As cadeias de caracteres são classificadas principalmente por comprimento e depois pela primeira letra da cadeia de caracteres, em ordem crescente.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a>Classificação decrescente secundária  
 O exemplo a seguir demonstra como usar o `Order By Descending` cláusula em uma consulta LINQ para executar uma classificação primária, em ordem crescente e uma classificação secundária, em ordem decrescente. As cadeias de caracteres são classificadas principalmente por comprimento e depois pela primeira letra da cadeia de caracteres.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Como: classificar resultados de consulta](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)   
 [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
