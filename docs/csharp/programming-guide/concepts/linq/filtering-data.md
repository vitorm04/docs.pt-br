---
title: "Filtragem de dados (c#) | Microsoft Docs"
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
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Filtragem de dados (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Filtragem refere\-se a operação de restringir o conjunto de resultados para conter apenas os elementos que satisfazem uma condição especificada. Ele também é conhecido como seleção.  
  
 A ilustração a seguir mostra os resultados de uma seqüência de caracteres de filtragem. O predicado para a operação de filtragem Especifica que o caractere deve ser 'A'.  
  
 ![Operação de filtragem de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ\_Filter")  
  
 Os métodos de operador de consulta padrão que executam a seleção são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|OfType|Seleciona valores, dependendo de sua capacidade de ser convertido em um tipo especificado.|Não aplicável.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|Where|Seleciona valores com base em uma função de predicado.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## Exemplo de sintaxe de expressão de consulta  
 O exemplo a seguir usa o `where` cláusula para filtrar em uma matriz essas cadeias de caracteres com um comprimento específico.  
  
```c#  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula where](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Como especificar filtros predicados dinamicamente em tempo de execução](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)   
 [How to: Query An Assembly's Metadata with Reflection \(LINQ\) \(C\#\)](../Topic/How%20to:%20Query%20An%20Assembly's%20Metadata%20with%20Reflection%20\(LINQ\)%20\(C%23\).md)   
 [Como: consultar arquivos com um atributo ou nome especificado \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)   
 [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)