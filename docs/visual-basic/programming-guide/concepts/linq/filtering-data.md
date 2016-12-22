---
title: "Filtragem de dados (Visual Basic) | Microsoft Docs"
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
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Filtragem de dados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Filtragem refere\-se a operação de restringir o conjunto de resultados para conter apenas os elementos que satisfazem uma condição especificada. Ele também é conhecido como seleção.  
  
 A ilustração a seguir mostra os resultados de uma seqüência de caracteres de filtragem. O predicado para a operação de filtragem Especifica que o caractere deve ser 'A'.  
  
 ![Operação de filtragem de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ\_Filter")  
  
 Os métodos de operador de consulta padrão que executam a seleção são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais Informações|  
|--------------------|---------------|------------------------------------------------------|----------------------|  
|OfType|Seleciona valores, dependendo de sua capacidade de ser convertido em um tipo especificado.|Não aplicável.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|Where|Seleciona valores com base em uma função de predicado.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## Exemplo de sintaxe de expressão de consulta  
 O exemplo a seguir usa o `Where` para filtrar em uma matriz essas cadeias de caracteres com um comprimento específico.  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Como filtrar resultados de consulta](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)   
 [How to: Query An Assembly's Metadata with Reflection \(LINQ\) \(Visual Basic\)](../Topic/How%20to:%20Query%20An%20Assembly's%20Metadata%20with%20Reflection%20\(LINQ\)%20\(Visual%20Basic\).md)   
 [Como: consultar arquivos com um atributo especificado ou o nome \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)   
 [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)