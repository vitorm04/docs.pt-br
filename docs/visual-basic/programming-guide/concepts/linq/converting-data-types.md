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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 948779e1648291b00a68bfd83d57750d48a9a6d8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="9489d-102">Convertendo tipos de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9489d-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="9489d-103">Métodos de conversão alterar o tipo de objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="9489d-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="9489d-104">Operações de conversão em consultas LINQ são úteis em uma variedade de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9489d-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="9489d-105">Estes são alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="9489d-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="9489d-106">O <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>método pode ser usado para ocultar a implementação personalizada do tipo de um operador de consulta padrão.</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="9489d-107">O <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>método pode ser usado para habilitar a coleções sem parâmetros de consulta LINQ.</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="9489d-108">O <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>métodos podem ser usados para forçar a execução imediata da consulta em vez de adiamento de até que a consulta é enumerada.</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9489d-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="9489d-109">Methods</span></span>  
 <span data-ttu-id="9489d-110">A tabela a seguir lista os métodos de operador de consulta padrão que executam conversões de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9489d-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="9489d-111">Os métodos de conversão nesta tabela cujos nomes começam com "Como" alterar o tipo estático da coleção de origem, mas não enumerar.</span><span class="sxs-lookup"><span data-stu-id="9489d-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="9489d-112">Digite os métodos cujos nomes começam com "Para enumerar a coleção de origem e colocar os itens na coleção correspondente".</span><span class="sxs-lookup"><span data-stu-id="9489d-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="9489d-113">Nome do método</span><span class="sxs-lookup"><span data-stu-id="9489d-113">Method Name</span></span>|<span data-ttu-id="9489d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9489d-114">Description</span></span>|<span data-ttu-id="9489d-115">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9489d-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9489d-116">Mais informações</span><span class="sxs-lookup"><span data-stu-id="9489d-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="9489d-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="9489d-117">AsEnumerable</span></span>|<span data-ttu-id="9489d-118">Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="9489d-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="9489d-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9489d-119">Not applicable.</span></span>|<span data-ttu-id="9489d-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9489d-121">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="9489d-121">AsQueryable</span></span>|<span data-ttu-id="9489d-122">Converte um (genérico) <xref:System.Collections.IEnumerable>para <xref:System.Linq.IQueryable>.</xref:System.Linq.IQueryable> (genérico)</xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="9489d-122">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="9489d-123">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9489d-123">Not applicable.</span></span>|<span data-ttu-id="9489d-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9489d-125">Conversão</span><span class="sxs-lookup"><span data-stu-id="9489d-125">Cast</span></span>|<span data-ttu-id="9489d-126">Converte os elementos de uma coleção para um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="9489d-126">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<span data-ttu-id="9489d-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="9489d-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9489d-129">OfType</span><span class="sxs-lookup"><span data-stu-id="9489d-129">OfType</span></span>|<span data-ttu-id="9489d-130">Filtros de valores, dependendo de sua capacidade de ser convertido em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="9489d-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="9489d-131">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9489d-131">Not applicable.</span></span>|<span data-ttu-id="9489d-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="9489d-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9489d-134">ToArray</span><span class="sxs-lookup"><span data-stu-id="9489d-134">ToArray</span></span>|<span data-ttu-id="9489d-135">Converte uma coleção para uma matriz.</span><span class="sxs-lookup"><span data-stu-id="9489d-135">Converts a collection to an array.</span></span> <span data-ttu-id="9489d-136">Esse método força a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="9489d-136">This method forces query execution.</span></span>|<span data-ttu-id="9489d-137">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9489d-137">Not applicable.</span></span>|<span data-ttu-id="9489d-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9489d-139">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="9489d-139">ToDictionary</span></span>|<span data-ttu-id="9489d-140">Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602>com base em uma função de seletor de chave.</xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="9489d-140">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="9489d-141">Esse método força a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="9489d-141">This method forces query execution.</span></span>|<span data-ttu-id="9489d-142">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9489d-142">Not applicable.</span></span>|<span data-ttu-id="9489d-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9489d-144">ToList</span><span class="sxs-lookup"><span data-stu-id="9489d-144">ToList</span></span>|<span data-ttu-id="9489d-145">Converte uma coleção para <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="9489d-145">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="9489d-146">Esse método força a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="9489d-146">This method forces query execution.</span></span>|<span data-ttu-id="9489d-147">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9489d-147">Not applicable.</span></span>|<span data-ttu-id="9489d-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9489d-149">ToLookup</span><span class="sxs-lookup"><span data-stu-id="9489d-149">ToLookup</span></span>|<span data-ttu-id="9489d-150">Coloca os elementos em um <xref:System.Linq.Lookup%602>(um dicionário de um-para-muitos) com base em uma função de seletor de chave.</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="9489d-150">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="9489d-151">Esse método força a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="9489d-151">This method forces query execution.</span></span>|<span data-ttu-id="9489d-152">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9489d-152">Not applicable.</span></span>|<span data-ttu-id="9489d-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9489d-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="9489d-154">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="9489d-154">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="9489d-155">O seguinte exemplo de código usa o `From As` cláusula para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.</span><span class="sxs-lookup"><span data-stu-id="9489d-155">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9489d-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9489d-156">See Also</span></span>  
 <span data-ttu-id="9489d-157"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="9489d-157"><xref:System.Linq></span></span>   
<span data-ttu-id="9489d-158"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="9489d-158"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="9489d-159"> [Cláusula FROM](../../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="9489d-159"> [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="9489d-160"> [Como: consultar um ArrayList com LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="9489d-160"> [How to: Query an ArrayList with LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span></span>
