---
title: Cláusula From (Visual Basic)
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
ms.openlocfilehash: 71573de48cc51c48291fc4b82a0628d2d0f96caa
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198238"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="9ff32-102">Cláusula From (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ff32-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="9ff32-103">Especifica uma ou mais variáveis de intervalo e uma coleção para consulta.</span><span class="sxs-lookup"><span data-stu-id="9ff32-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff32-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ff32-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9ff32-105">Partes</span><span class="sxs-lookup"><span data-stu-id="9ff32-105">Parts</span></span>  
  
|<span data-ttu-id="9ff32-106">Termo</span><span class="sxs-lookup"><span data-stu-id="9ff32-106">Term</span></span>|<span data-ttu-id="9ff32-107">Definição</span><span class="sxs-lookup"><span data-stu-id="9ff32-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="9ff32-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9ff32-108">Required.</span></span> <span data-ttu-id="9ff32-109">Um *variável de intervalo* usado para iterar por meio dos elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="9ff32-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="9ff32-110">Uma variável de intervalo é usada para se referir a cada membro do `collection` como a consulta itera por meio de `collection`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="9ff32-111">Deve ser um tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="9ff32-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="9ff32-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9ff32-112">Optional.</span></span> <span data-ttu-id="9ff32-113">O tipo de `element`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-113">The type of `element`.</span></span> <span data-ttu-id="9ff32-114">Se nenhum `type` for especificado, o tipo de `element` é inferido do `collection`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="9ff32-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9ff32-115">Required.</span></span> <span data-ttu-id="9ff32-116">Refere-se à coleção a ser consultado.</span><span class="sxs-lookup"><span data-stu-id="9ff32-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="9ff32-117">Deve ser um tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="9ff32-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ff32-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ff32-118">Remarks</span></span>  
 <span data-ttu-id="9ff32-119">O `From` cláusula é usada para identificar os dados de origem para uma consulta e as variáveis que são usadas para se referir a um elemento da coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="9ff32-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="9ff32-120">Essas variáveis são chamadas *variáveis de alcance*.</span><span class="sxs-lookup"><span data-stu-id="9ff32-120">These variables are called *range variables*.</span></span> <span data-ttu-id="9ff32-121">O `From` cláusula é necessária para uma consulta, exceto quando o `Aggregate` cláusula é usada para identificar uma consulta que retorna somente resultados agregados.</span><span class="sxs-lookup"><span data-stu-id="9ff32-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="9ff32-122">Para obter mais informações, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9ff32-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="9ff32-123">Você pode especificar vários `From` cláusulas em uma consulta para identificar várias coleções a serem agrupadas.</span><span class="sxs-lookup"><span data-stu-id="9ff32-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="9ff32-124">Quando várias coleções são especificadas, elas são iteradas de forma independente ou uni-los se eles estão relacionados.</span><span class="sxs-lookup"><span data-stu-id="9ff32-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="9ff32-125">Você pode associar coleções implicitamente, usando o `Select` cláusula, ou explicitamente, usando o `Join` ou `Group Join` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="9ff32-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="9ff32-126">Como alternativa, você pode especificar diversas variáveis de alcance e coleções em uma única `From` cláusula, com cada variável de alcance e coleção separados dos outros por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="9ff32-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="9ff32-127">O exemplo de código a seguir mostra as duas opções de sintaxe para o `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="9ff32-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="9ff32-128">O `From` cláusula define o escopo de uma consulta, que é semelhante ao escopo de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="9ff32-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="9ff32-129">Portanto, cada `element` variável de intervalo no escopo de uma consulta deve ter um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9ff32-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="9ff32-130">Porque você pode especificar vários `From` cláusulas para uma consulta subsequente `From` cláusulas podem se referir a variáveis de intervalo na `From` cláusula, ou eles podem consultar variáveis de alcance em um anterior `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="9ff32-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="9ff32-131">Por exemplo, o exemplo a seguir mostra um aninhada `From` cláusula onde a coleção na segunda cláusula é baseada em uma propriedade da variável de intervalo na primeira cláusula.</span><span class="sxs-lookup"><span data-stu-id="9ff32-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="9ff32-132">Cada `From` cláusula pode ser seguida por qualquer combinação de cláusulas de consulta adicionais para refinar a consulta.</span><span class="sxs-lookup"><span data-stu-id="9ff32-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="9ff32-133">Você pode refinar a consulta das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="9ff32-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="9ff32-134">Combinar várias coleções implicitamente, usando o `From` e `Select` cláusulas, ou explicitamente, usando o `Join` ou `Group Join` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="9ff32-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="9ff32-135">Use o `Where` cláusula para filtrar o resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="9ff32-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="9ff32-136">Classificar o resultado usando o `Order By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="9ff32-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="9ff32-137">Agrupar resultados semelhantes usando a `Group By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="9ff32-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="9ff32-138">Use o `Aggregate` cláusula para identificar as funções de agregação a ser avaliada para o resultado da consulta inteira.</span><span class="sxs-lookup"><span data-stu-id="9ff32-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="9ff32-139">Use o `Let` cláusula para introduzir uma variável de iteração cujo valor é determinado por uma expressão em vez de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9ff32-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="9ff32-140">Use o `Distinct` cláusula para ignorar os resultados da consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="9ff32-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="9ff32-141">Identificar as partes do resultado para retornar usando o `Skip`, `Take`, `Skip While`, e `Take While` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="9ff32-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ff32-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ff32-142">Example</span></span>  
 <span data-ttu-id="9ff32-143">A seguinte consulta de expressão usa uma `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção.</span><span class="sxs-lookup"><span data-stu-id="9ff32-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="9ff32-144">O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada.</span><span class="sxs-lookup"><span data-stu-id="9ff32-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="9ff32-145">O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="9ff32-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9ff32-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ff32-146">See Also</span></span>  
 [<span data-ttu-id="9ff32-147">Consultas</span><span class="sxs-lookup"><span data-stu-id="9ff32-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="9ff32-148">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ff32-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9ff32-149">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="9ff32-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="9ff32-150">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="9ff32-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="9ff32-151">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="9ff32-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="9ff32-152">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="9ff32-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="9ff32-153">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="9ff32-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="9ff32-154">Cláusula Distinct</span><span class="sxs-lookup"><span data-stu-id="9ff32-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="9ff32-155">Cláusula Join</span><span class="sxs-lookup"><span data-stu-id="9ff32-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="9ff32-156">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="9ff32-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="9ff32-157">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="9ff32-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="9ff32-158">Cláusula Let</span><span class="sxs-lookup"><span data-stu-id="9ff32-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="9ff32-159">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="9ff32-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="9ff32-160">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="9ff32-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="9ff32-161">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="9ff32-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="9ff32-162">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="9ff32-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
