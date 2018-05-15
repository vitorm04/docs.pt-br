---
title: Convertendo tipos de dados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 9821b2d6caad8feeac856185b92518c25de88da3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="b7634-102">Convertendo tipos de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7634-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="b7634-103">Os métodos de conversão alteram o tipo dos objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="b7634-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="b7634-104">As operações de conversão em consultas LINQ são úteis em diversas aplicações.</span><span class="sxs-lookup"><span data-stu-id="b7634-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="b7634-105">A seguir estão alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="b7634-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="b7634-106">O método <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> pode ser usado para ocultar a implementação personalizada de um tipo de um operador de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="b7634-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="b7634-107">O método <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> pode ser usado para habilitar coleções sem parâmetros para consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="b7634-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="b7634-108">Os métodos <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> podem ser usados para forçar a execução de consulta imediata em vez de adiá-la até que a consulta seja enumerada.</span><span class="sxs-lookup"><span data-stu-id="b7634-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7634-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="b7634-109">Methods</span></span>  
 <span data-ttu-id="b7634-110">A tabela a seguir lista os métodos de operador de consulta padrão que realizam conversões de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b7634-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="b7634-111">Os métodos de conversão nesta tabela cujos nomes começam com "As" alteram o tipo estático da coleção de origem, mas não a enumeram.</span><span class="sxs-lookup"><span data-stu-id="b7634-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="b7634-112">Os métodos cujos nomes começam com "To" enumeram a coleção de origem e colocam os itens na coleção de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="b7634-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="b7634-113">Nome do método</span><span class="sxs-lookup"><span data-stu-id="b7634-113">Method Name</span></span>|<span data-ttu-id="b7634-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7634-114">Description</span></span>|<span data-ttu-id="b7634-115">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7634-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b7634-116">Mais informações</span><span class="sxs-lookup"><span data-stu-id="b7634-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b7634-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="b7634-117">AsEnumerable</span></span>|<span data-ttu-id="b7634-118">Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b7634-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="b7634-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b7634-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7634-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="b7634-120">AsQueryable</span></span>|<span data-ttu-id="b7634-121">Converte um <xref:System.Collections.IEnumerable> (genérico) em um <xref:System.Linq.IQueryable> (genérico).</span><span class="sxs-lookup"><span data-stu-id="b7634-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="b7634-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b7634-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7634-123">Conversão</span><span class="sxs-lookup"><span data-stu-id="b7634-123">Cast</span></span>|<span data-ttu-id="b7634-124">Converte os elementos de uma coleção em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="b7634-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7634-125">OfType</span><span class="sxs-lookup"><span data-stu-id="b7634-125">OfType</span></span>|<span data-ttu-id="b7634-126">Filtra valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="b7634-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="b7634-127">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b7634-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7634-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="b7634-128">ToArray</span></span>|<span data-ttu-id="b7634-129">Converte uma coleção em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="b7634-129">Converts a collection to an array.</span></span> <span data-ttu-id="b7634-130">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="b7634-130">This method forces query execution.</span></span>|<span data-ttu-id="b7634-131">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b7634-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7634-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="b7634-132">ToDictionary</span></span>|<span data-ttu-id="b7634-133">Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="b7634-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="b7634-134">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="b7634-134">This method forces query execution.</span></span>|<span data-ttu-id="b7634-135">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b7634-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7634-136">ToList</span><span class="sxs-lookup"><span data-stu-id="b7634-136">ToList</span></span>|<span data-ttu-id="b7634-137">Converte uma coleção em um <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="b7634-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="b7634-138">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="b7634-138">This method forces query execution.</span></span>|<span data-ttu-id="b7634-139">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b7634-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7634-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="b7634-140">ToLookup</span></span>|<span data-ttu-id="b7634-141">Coloca os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="b7634-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="b7634-142">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="b7634-142">This method forces query execution.</span></span>|<span data-ttu-id="b7634-143">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b7634-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b7634-144">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="b7634-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b7634-145">O seguinte exemplo de código usa o `From As` cláusula para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.</span><span class="sxs-lookup"><span data-stu-id="b7634-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7634-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7634-146">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="b7634-147">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7634-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="b7634-148">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="b7634-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="b7634-149">Como: consultar um ArrayList com LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7634-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
