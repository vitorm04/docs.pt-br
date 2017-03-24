---
title: Convertendo tipos de dados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
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
ms.openlocfilehash: 53d8ad292891a567e13ec8a5396bcc114b379351
ms.lasthandoff: 03/13/2017

---
# <a name="converting-data-types-visual-basic"></a>Convertendo tipos de dados (Visual Basic)
Métodos de conversão alterar o tipo de objetos de entrada.  
  
 Operações de conversão em consultas LINQ são úteis em uma variedade de aplicativos. Estes são alguns exemplos:  
  
-   O <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>método pode ser usado para ocultar a implementação personalizada do tipo de um operador de consulta padrão.</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>  
  
-   O <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>método pode ser usado para habilitar a coleções sem parâmetros de consulta LINQ.</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>  
  
-   O <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>métodos podem ser usados para forçar a execução imediata da consulta em vez de adiamento de até que a consulta é enumerada.</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos de operador de consulta padrão que executam conversões de tipo de dados.  
  
 Os métodos de conversão nesta tabela cujos nomes começam com "Como" alterar o tipo estático da coleção de origem, mas não enumerar. Digite os métodos cujos nomes começam com "Para enumerar a coleção de origem e colocar os itens na coleção correspondente".  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>|Não aplicável.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|Converte um (genérico) <xref:System.Collections.IEnumerable>para <xref:System.Linq.IQueryable>.</xref:System.Linq.IQueryable> (genérico)</xref:System.Collections.IEnumerable>|Não aplicável.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Conversão|Converte os elementos de uma coleção para um tipo especificado.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|Filtros de valores, dependendo de sua capacidade de ser convertido em um tipo especificado.|Não aplicável.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|Converte uma coleção para uma matriz. Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602>com base em uma função de seletor de chave.</xref:System.Collections.Generic.Dictionary%602> Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|Converte uma coleção para <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601> Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|Coloca os elementos em um <xref:System.Linq.Lookup%602>(um dicionário de um-para-muitos) com base em uma função de seletor de chave.</xref:System.Linq.Lookup%602> Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemplo de sintaxe de expressão de consulta  
 O seguinte exemplo de código usa o `From As` cláusula para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula FROM](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [Como: consultar um ArrayList com LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
