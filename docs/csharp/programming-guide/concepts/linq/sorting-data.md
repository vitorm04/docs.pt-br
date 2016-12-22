---
title: "Classificando dados (c#) | Microsoft Docs"
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
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Classificando dados (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma operação de classificação ordena os elementos de uma sequência com base em um ou mais atributos. O primeiro critério de classificação executa uma classificação primária nos elementos. Especificando um segundo critério de classificação, você pode classificar os elementos dentro de cada grupo de classificação principal.  
  
 A ilustração a seguir mostra os resultados de uma operação de classificação alfabética em uma seqüência de caracteres.  
  
 ![Operação de classificação LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ\_Ordering")  
  
 Os métodos de operador de consulta padrão que classificam dados são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|OrderBy|Classifica valores em ordem crescente.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName>|  
|OrderByDescending|Classifica valores em ordem decrescente.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName>|  
|ThenBy|Executa uma classificação secundária em ordem crescente.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName>|  
|ThenByDescending|Executa uma classificação secundária em ordem decrescente.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName>|  
|Reverter|Inverte a ordem dos elementos em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName>|  
  
## Exemplos de sintaxe de expressão de consulta  
  
### Exemplos de classificação principal  
  
#### Classificação crescente primária  
 O exemplo a seguir demonstra como usar o `orderby` cláusula em uma consulta LINQ para classificar as cadeias de caracteres em uma matriz de comprimento de cadeia de caracteres, em ordem crescente.  
  
```c#  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### Classificação decrescente primária  
 O exemplo a seguir demonstra como usar o `orderby``descending` cláusula em uma consulta LINQ para classificar as cadeias de caracteres pela sua primeira letra, em ordem decrescente.  
  
```c#  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### Exemplos de classificação secundária  
  
#### Classificação crescente secundária  
 O exemplo a seguir demonstra como usar o `orderby` cláusula em uma consulta LINQ para executar uma classificação primária e secundária das cadeias de caracteres em uma matriz. As cadeias de caracteres são classificadas principalmente por comprimento e depois pela primeira letra da cadeia de caracteres, em ordem crescente.  
  
```c#  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### Classificação decrescente secundária  
 O exemplo a seguir demonstra como usar o `orderby``descending` cláusula em uma consulta LINQ para executar uma classificação primária, em ordem crescente e uma classificação secundária, em ordem decrescente. As cadeias de caracteres são classificadas principalmente por comprimento e depois pela primeira letra da cadeia de caracteres.  
  
```c#  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md)   
 [Como ordenar os resultados de uma cláusula join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)   
 [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)