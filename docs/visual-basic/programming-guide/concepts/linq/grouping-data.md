---
title: Agrupando dados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d89ae6d155ab901b03cf92a7508261fb147b97b7
ms.lasthandoff: 03/13/2017

---
# <a name="grouping-data-visual-basic"></a>Agrupando dados (Visual Basic)
Agrupamento refere-se a operação de colocar dados em grupos para que os elementos em cada grupo compartilham um atributo comum.  
  
 A ilustração a seguir mostra os resultados de uma sequência de caracteres de agrupamento. A chave para cada grupo é o caractere.  
  
 ![Operações de agrupamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 Os métodos de operador de consulta padrão que agrupam os elementos de dados são listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Agrupa elementos que compartilham um atributo comum. Cada grupo é representado por um <xref:System.Linq.IGrouping%602>objeto.</xref:System.Linq.IGrouping%602>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName>|  
|ToLookup|Insere elementos em um <xref:System.Linq.Lookup%602>(um dicionário de um-para-muitos) com base em uma função de seletor de chave.</xref:System.Linq.Lookup%602>|Não aplicável.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemplo de sintaxe de expressão de consulta  
 O seguinte exemplo de código usa o `Group By` cláusula para inteiros de grupo em uma lista se elas estiverem par ou ímpar.  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md)   
 [Como: agrupar arquivos por extensão (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)   
 [Como: dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
