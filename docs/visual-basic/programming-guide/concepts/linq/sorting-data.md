---
title: Classificando dados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: 5875b15dbdec69aca653b8f6cca4dd07fc9af343
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126247"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="6da5a-102">Classificando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6da5a-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="6da5a-103">Uma operação de classificação ordena os elementos de uma sequência com base em um ou mais atributos.</span><span class="sxs-lookup"><span data-stu-id="6da5a-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="6da5a-104">O primeiro critério de classificação executa uma classificação primária dos elementos.</span><span class="sxs-lookup"><span data-stu-id="6da5a-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="6da5a-105">Especificando um segundo critério de classificação, você pode classificar os elementos dentro de cada grupo de classificação primário.</span><span class="sxs-lookup"><span data-stu-id="6da5a-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="6da5a-106">A ilustração a seguir mostra os resultados de uma operação de classificação alfabética em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6da5a-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 ![Gráfico que mostra uma operação de classificação em ordem alfabética.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="6da5a-108">Os métodos de operador de consulta padrão que classificam dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="6da5a-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6da5a-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="6da5a-109">Methods</span></span>  
  
|<span data-ttu-id="6da5a-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="6da5a-110">Method Name</span></span>|<span data-ttu-id="6da5a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6da5a-111">Description</span></span>|<span data-ttu-id="6da5a-112">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6da5a-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6da5a-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6da5a-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="6da5a-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="6da5a-114">OrderBy</span></span>|<span data-ttu-id="6da5a-115">Classifica valores em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6da5a-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="6da5a-116">OrderByDescending</span></span>|<span data-ttu-id="6da5a-117">Classifica valores em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6da5a-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="6da5a-118">ThenBy</span></span>|<span data-ttu-id="6da5a-119">Executa uma classificação secundária em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6da5a-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="6da5a-120">ThenByDescending</span></span>|<span data-ttu-id="6da5a-121">Executa uma classificação secundária em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6da5a-122">Inverso</span><span class="sxs-lookup"><span data-stu-id="6da5a-122">Reverse</span></span>|<span data-ttu-id="6da5a-123">Inverte a ordem dos elementos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="6da5a-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="6da5a-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6da5a-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6da5a-125">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="6da5a-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="6da5a-126">Exemplos de classificação primária</span><span class="sxs-lookup"><span data-stu-id="6da5a-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="6da5a-127">Classificação crescente primária</span><span class="sxs-lookup"><span data-stu-id="6da5a-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="6da5a-128">O exemplo a seguir demonstra como usar a cláusula `Order By` em uma consulta de LINQ para classificar as cadeias de caracteres em uma matriz segundo o tamanho da cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="6da5a-129">Classificação decrescente primária</span><span class="sxs-lookup"><span data-stu-id="6da5a-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="6da5a-130">O exemplo seguinte demonstra como usar a cláusula `Order By Descending` em uma consulta de LINQ para classificar as cadeias de caracteres segundo sua primeira letra, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="6da5a-131">Exemplos de classificação secundária</span><span class="sxs-lookup"><span data-stu-id="6da5a-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="6da5a-132">Classificação crescente secundária</span><span class="sxs-lookup"><span data-stu-id="6da5a-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="6da5a-133">O exemplo a seguir demonstra como usar a cláusula `Order By` em uma consulta de LINQ para executar uma classificação primária e uma classificação secundária das cadeias de caracteres em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="6da5a-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="6da5a-134">As cadeias de caracteres são classificadas primeiro segundo o tamanho e, depois, segundo a primeira letra da cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="6da5a-135">Classificação decrescente secundária</span><span class="sxs-lookup"><span data-stu-id="6da5a-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="6da5a-136">O exemplo seguinte demonstra como usar a cláusula `Order By Descending` em uma consulta de LINQ para executar uma classificação primária, em ordem crescente e uma classificação secundária, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="6da5a-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="6da5a-137">As cadeias de caracteres são classificadas primeiro segundo o tamanho e, depois, segundo a primeira letra da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6da5a-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6da5a-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6da5a-138">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="6da5a-139">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6da5a-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6da5a-140">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="6da5a-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="6da5a-141">Como: Classificar os resultados de consulta</span><span class="sxs-lookup"><span data-stu-id="6da5a-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="6da5a-142">Como: Classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6da5a-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
