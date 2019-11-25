---
title: Cláusula From
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: a63fb41fc2b0ad885acf76ad5d56e446922f5b90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343773"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="36f90-102">Cláusula From (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36f90-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="36f90-103">Specifies one or more range variables and a collection to query.</span><span class="sxs-lookup"><span data-stu-id="36f90-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f90-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36f90-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="36f90-105">Partes</span><span class="sxs-lookup"><span data-stu-id="36f90-105">Parts</span></span>  
  
|<span data-ttu-id="36f90-106">Termo</span><span class="sxs-lookup"><span data-stu-id="36f90-106">Term</span></span>|<span data-ttu-id="36f90-107">Definição</span><span class="sxs-lookup"><span data-stu-id="36f90-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="36f90-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="36f90-108">Required.</span></span> <span data-ttu-id="36f90-109">A *range variable* used to iterate through the elements of the collection.</span><span class="sxs-lookup"><span data-stu-id="36f90-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="36f90-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span><span class="sxs-lookup"><span data-stu-id="36f90-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="36f90-111">Must be an enumerable type.</span><span class="sxs-lookup"><span data-stu-id="36f90-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="36f90-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="36f90-112">Optional.</span></span> <span data-ttu-id="36f90-113">O tipo de `element`.</span><span class="sxs-lookup"><span data-stu-id="36f90-113">The type of `element`.</span></span> <span data-ttu-id="36f90-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span><span class="sxs-lookup"><span data-stu-id="36f90-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="36f90-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="36f90-115">Required.</span></span> <span data-ttu-id="36f90-116">Refers to the collection to be queried.</span><span class="sxs-lookup"><span data-stu-id="36f90-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="36f90-117">Must be an enumerable type.</span><span class="sxs-lookup"><span data-stu-id="36f90-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36f90-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="36f90-118">Remarks</span></span>  
 <span data-ttu-id="36f90-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span><span class="sxs-lookup"><span data-stu-id="36f90-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="36f90-120">These variables are called *range variables*.</span><span class="sxs-lookup"><span data-stu-id="36f90-120">These variables are called *range variables*.</span></span> <span data-ttu-id="36f90-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span><span class="sxs-lookup"><span data-stu-id="36f90-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="36f90-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="36f90-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="36f90-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span><span class="sxs-lookup"><span data-stu-id="36f90-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="36f90-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span><span class="sxs-lookup"><span data-stu-id="36f90-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="36f90-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span><span class="sxs-lookup"><span data-stu-id="36f90-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="36f90-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span><span class="sxs-lookup"><span data-stu-id="36f90-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="36f90-127">The following code example shows both syntax options for the `From` clause.</span><span class="sxs-lookup"><span data-stu-id="36f90-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="36f90-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span><span class="sxs-lookup"><span data-stu-id="36f90-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="36f90-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span><span class="sxs-lookup"><span data-stu-id="36f90-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="36f90-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span><span class="sxs-lookup"><span data-stu-id="36f90-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="36f90-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span><span class="sxs-lookup"><span data-stu-id="36f90-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="36f90-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span><span class="sxs-lookup"><span data-stu-id="36f90-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="36f90-133">You can refine the query in the following ways:</span><span class="sxs-lookup"><span data-stu-id="36f90-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="36f90-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span><span class="sxs-lookup"><span data-stu-id="36f90-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="36f90-135">Use the `Where` clause to filter the query result.</span><span class="sxs-lookup"><span data-stu-id="36f90-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="36f90-136">Sort the result by using the `Order By` clause.</span><span class="sxs-lookup"><span data-stu-id="36f90-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="36f90-137">Group similar results together by using the `Group By` clause.</span><span class="sxs-lookup"><span data-stu-id="36f90-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="36f90-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span><span class="sxs-lookup"><span data-stu-id="36f90-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="36f90-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span><span class="sxs-lookup"><span data-stu-id="36f90-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="36f90-140">Use the `Distinct` clause to ignore duplicate query results.</span><span class="sxs-lookup"><span data-stu-id="36f90-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="36f90-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span><span class="sxs-lookup"><span data-stu-id="36f90-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36f90-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36f90-142">Example</span></span>  
 <span data-ttu-id="36f90-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span><span class="sxs-lookup"><span data-stu-id="36f90-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="36f90-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span><span class="sxs-lookup"><span data-stu-id="36f90-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="36f90-145">The `For Each` loop displays the company name for each customer in the query result.</span><span class="sxs-lookup"><span data-stu-id="36f90-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="36f90-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36f90-146">See also</span></span>

- [<span data-ttu-id="36f90-147">Consultas</span><span class="sxs-lookup"><span data-stu-id="36f90-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="36f90-148">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36f90-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="36f90-149">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="36f90-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="36f90-150">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="36f90-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="36f90-151">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="36f90-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="36f90-152">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="36f90-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="36f90-153">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="36f90-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="36f90-154">Cláusula Distinct</span><span class="sxs-lookup"><span data-stu-id="36f90-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="36f90-155">Cláusula Join</span><span class="sxs-lookup"><span data-stu-id="36f90-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="36f90-156">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="36f90-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="36f90-157">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="36f90-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="36f90-158">Cláusula Let</span><span class="sxs-lookup"><span data-stu-id="36f90-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="36f90-159">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="36f90-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="36f90-160">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="36f90-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="36f90-161">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="36f90-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="36f90-162">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="36f90-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
