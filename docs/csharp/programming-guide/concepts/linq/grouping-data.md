---
title: "Agrupando dados (c#) | Microsoft Docs"
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
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Agrupando dados (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Agrupamento refere\-se a operação de colocar dados em grupos para que os elementos em cada grupo compartilham um atributo comum.  
  
 A ilustração a seguir mostra os resultados de uma seqüência de caracteres de agrupamento. A chave para cada grupo é o caractere.  
  
 ![Operações de agrupamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ\_Group")  
  
 Os métodos de operador de consulta padrão que agrupam os elementos de dados são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|GroupBy|Agrupa elementos que compartilham um atributo comum. Cada grupo é representado por um <xref:System.Linq.IGrouping%602> objeto.|`group … by`<br /><br /> \- ou \-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName>|  
|ToLookup|Insere elementos em um <xref:System.Linq.Lookup%602> \(um dicionário de um\-para\-muitos\) com base em uma função de seletor de chave.|Não aplicável.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## Exemplo de sintaxe de expressão de consulta  
 O seguinte exemplo de código usa o `group by` cláusula para inteiros de grupo em uma lista se elas estiverem par ou ímpar.  
  
```c#  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md)   
 [Como criar um grupo aninhado](../Topic/How%20to:%20Create%20a%20Nested%20Group%20\(C%23%20Programming%20Guide\).md)   
 [Como: agrupar arquivos por extensão \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)   
 [Como agrupar resultados de consultas](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)   
 [Como executar uma subconsulta em uma operação de agrupamento](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)   
 [Como: dividir um arquivo em vários arquivos usando grupos \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)