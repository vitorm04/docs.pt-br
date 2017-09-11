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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1870d401ffdeeb2452ace1b74a8fb70e19c9b9ed
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="4101e-102">Classificando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4101e-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="4101e-103">Uma operação de classificação ordena os elementos de uma sequência com base em um ou mais atributos.</span><span class="sxs-lookup"><span data-stu-id="4101e-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="4101e-104">O primeiro critério de classificação executa uma classificação primária nos elementos.</span><span class="sxs-lookup"><span data-stu-id="4101e-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="4101e-105">Especificando um segundo critério de classificação, você pode classificar os elementos dentro de cada grupo de classificação principal.</span><span class="sxs-lookup"><span data-stu-id="4101e-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="4101e-106">A ilustração a seguir mostra os resultados de uma operação de classificação alfabética em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4101e-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="4101e-107">![Operação de classificação de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="4101e-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="4101e-108">Os métodos de operador de consulta padrão que classificam dados são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="4101e-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4101e-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="4101e-109">Methods</span></span>  
  
|<span data-ttu-id="4101e-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="4101e-110">Method Name</span></span>|<span data-ttu-id="4101e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="4101e-111">Description</span></span>|<span data-ttu-id="4101e-112">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4101e-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="4101e-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="4101e-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="4101e-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="4101e-114">OrderBy</span></span>|<span data-ttu-id="4101e-115">Classifica valores em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-115">Sorts values in ascending order.</span></span>|`Order By`|<span data-ttu-id="4101e-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4101e-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="4101e-118">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="4101e-118">OrderByDescending</span></span>|<span data-ttu-id="4101e-119">Classifica valores em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-119">Sorts values in descending order.</span></span>|`Order By … Descending`|<span data-ttu-id="4101e-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4101e-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="4101e-122">ThenBy</span><span class="sxs-lookup"><span data-stu-id="4101e-122">ThenBy</span></span>|<span data-ttu-id="4101e-123">Executa uma classificação secundária em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-123">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<span data-ttu-id="4101e-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4101e-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="4101e-126">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="4101e-126">ThenByDescending</span></span>|<span data-ttu-id="4101e-127">Executa uma classificação secundária em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-127">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<span data-ttu-id="4101e-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4101e-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="4101e-130">Inverso</span><span class="sxs-lookup"><span data-stu-id="4101e-130">Reverse</span></span>|<span data-ttu-id="4101e-131">Inverte a ordem dos elementos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="4101e-131">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="4101e-132">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="4101e-132">Not applicable.</span></span>|<span data-ttu-id="4101e-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4101e-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4101e-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="4101e-135">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="4101e-135">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="4101e-136">Exemplos de classificação principal</span><span class="sxs-lookup"><span data-stu-id="4101e-136">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="4101e-137">Classificação crescente primária</span><span class="sxs-lookup"><span data-stu-id="4101e-137">Primary Ascending Sort</span></span>  
 <span data-ttu-id="4101e-138">O exemplo a seguir demonstra como usar o `Order By` cláusula em uma consulta LINQ para classificar as cadeias de caracteres em uma matriz de comprimento de cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-138">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="4101e-139">Classificação decrescente primária</span><span class="sxs-lookup"><span data-stu-id="4101e-139">Primary Descending Sort</span></span>  
 <span data-ttu-id="4101e-140">O exemplo a seguir demonstra como usar o `Order By Descending` cláusula em uma consulta LINQ para classificar as cadeias de caracteres pela sua primeira letra, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-140">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="4101e-141">Exemplos de classificação secundária</span><span class="sxs-lookup"><span data-stu-id="4101e-141">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="4101e-142">Classificação crescente secundária</span><span class="sxs-lookup"><span data-stu-id="4101e-142">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="4101e-143">O exemplo a seguir demonstra como usar o `Order By` cláusula em uma consulta LINQ para executar uma classificação primária e secundária das cadeias de caracteres em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="4101e-143">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="4101e-144">As cadeias de caracteres são classificadas principalmente por comprimento e depois pela primeira letra da cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-144">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="4101e-145">Classificação decrescente secundária</span><span class="sxs-lookup"><span data-stu-id="4101e-145">Secondary Descending Sort</span></span>  
 <span data-ttu-id="4101e-146">O exemplo a seguir demonstra como usar o `Order By Descending` cláusula em uma consulta LINQ para executar uma classificação primária, em ordem crescente e uma classificação secundária, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="4101e-146">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="4101e-147">As cadeias de caracteres são classificadas principalmente por comprimento e depois pela primeira letra da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4101e-147">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4101e-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4101e-148">See Also</span></span>  
 <span data-ttu-id="4101e-149"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="4101e-149"><xref:System.Linq></span></span>   
<span data-ttu-id="4101e-150"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4101e-150"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="4101e-151"> [Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4101e-151"> [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="4101e-152"> [Como: classificar resultados de consulta](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="4101e-152"> [How to: Sort Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="4101e-153"> [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="4101e-153"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
