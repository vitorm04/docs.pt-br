---
title: "Cláusula From (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], From
- From clause
- From statement
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cd5fd972ed800b6dd27969222b28b2559a1d01af
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="e09d3-102">Cláusula From (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e09d3-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="e09d3-103">Especifica uma ou mais variáveis intervalo e uma coleção para consulta.</span><span class="sxs-lookup"><span data-stu-id="e09d3-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e09d3-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e09d3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e09d3-105">Parts</span></span>  
  
|<span data-ttu-id="e09d3-106">Termo</span><span class="sxs-lookup"><span data-stu-id="e09d3-106">Term</span></span>|<span data-ttu-id="e09d3-107">Definição</span><span class="sxs-lookup"><span data-stu-id="e09d3-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="e09d3-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e09d3-108">Required.</span></span> <span data-ttu-id="e09d3-109">A *variável de intervalo* usado para percorrer os elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="e09d3-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="e09d3-110">Uma variável de alcance é usada para se referir a cada membro do `collection` como a consulta itera por meio de `collection`.</span><span class="sxs-lookup"><span data-stu-id="e09d3-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="e09d3-111">Deve ser um tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="e09d3-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="e09d3-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e09d3-112">Optional.</span></span> <span data-ttu-id="e09d3-113">O tipo de `element`.</span><span class="sxs-lookup"><span data-stu-id="e09d3-113">The type of `element`.</span></span> <span data-ttu-id="e09d3-114">Se nenhum `type` for especificado, o tipo de `element` é inferido do `collection`.</span><span class="sxs-lookup"><span data-stu-id="e09d3-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="e09d3-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e09d3-115">Required.</span></span> <span data-ttu-id="e09d3-116">Refere-se à coleção a ser consultado.</span><span class="sxs-lookup"><span data-stu-id="e09d3-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="e09d3-117">Deve ser um tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="e09d3-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e09d3-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="e09d3-118">Remarks</span></span>  
 <span data-ttu-id="e09d3-119">O `From` cláusula é usada para identificar a fonte de dados para uma consulta e as variáveis que são usadas para se referir a um elemento da coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="e09d3-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="e09d3-120">Essas variáveis são chamadas *variáveis de alcance*.</span><span class="sxs-lookup"><span data-stu-id="e09d3-120">These variables are called *range variables*.</span></span> <span data-ttu-id="e09d3-121">O `From` cláusula é necessária para uma consulta, exceto quando o `Aggregate` cláusula é usada para identificar uma consulta que retorna somente resultados agregados.</span><span class="sxs-lookup"><span data-stu-id="e09d3-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="e09d3-122">Para obter mais informações, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e09d3-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="e09d3-123">Você pode especificar várias `From` cláusulas em uma consulta para identificar várias coleções a serem unidas.</span><span class="sxs-lookup"><span data-stu-id="e09d3-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="e09d3-124">Quando várias coleções são especificadas, elas são iterados através de maneira independente, ou você pode associá-los se eles estão relacionados.</span><span class="sxs-lookup"><span data-stu-id="e09d3-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="e09d3-125">Você pode associar coleções implicitamente usando a `Select` cláusula, ou explicitamente, usando o `Join` ou `Group Join` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="e09d3-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="e09d3-126">Como alternativa, você pode especificar diversas variáveis de alcance e coleções em uma única `From` cláusula, com cada variável de alcance e coleção separados dos outros por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="e09d3-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="e09d3-127">O exemplo de código a seguir mostra as duas opções de sintaxe para o `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e09d3-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 <span data-ttu-id="e09d3-128">[!code-vb[VbSimpleQuerySamples&#21;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e09d3-128">[!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]</span></span>  
  
 <span data-ttu-id="e09d3-129">O `From` cláusula define o escopo de uma consulta, que é semelhante ao escopo de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="e09d3-129">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="e09d3-130">Portanto, cada `element` variável de intervalo no escopo de uma consulta deve ter um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="e09d3-130">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="e09d3-131">Porque você pode especificar várias `From` cláusulas para uma consulta, subsequentes `From` cláusulas podem fazer referência a variáveis de alcance no `From` cláusula, ou eles podem consultar variáveis de alcance na anterior `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e09d3-131">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="e09d3-132">Por exemplo, o exemplo a seguir mostra uma construção `From` cláusula onde a coleção na segunda cláusula é baseada em uma propriedade da variável de intervalo na primeira cláusula.</span><span class="sxs-lookup"><span data-stu-id="e09d3-132">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 <span data-ttu-id="e09d3-133">[!code-vb[VbSimpleQuerySamples&#22;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e09d3-133">[!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]</span></span>  
  
 <span data-ttu-id="e09d3-134">Cada `From` cláusula pode ser seguida por qualquer combinação de cláusulas de consulta adicionais para refinar a consulta.</span><span class="sxs-lookup"><span data-stu-id="e09d3-134">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="e09d3-135">Você pode refinar a consulta das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="e09d3-135">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="e09d3-136">Combinar várias coleções implicitamente usando a `From` e `Select` cláusulas, ou explicitamente, usando o `Join` ou `Group Join` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="e09d3-136">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="e09d3-137">Use o `Where` cláusula para filtrar o resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="e09d3-137">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="e09d3-138">Classifique os resultados usando o `Order By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e09d3-138">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="e09d3-139">Agrupar resultados semelhantes usando a `Group By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e09d3-139">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="e09d3-140">Use o `Aggregate` cláusula para identificar as funções agregadas para avaliar para o resultado da consulta inteira.</span><span class="sxs-lookup"><span data-stu-id="e09d3-140">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="e09d3-141">Use o `Let` cláusula para introduzir uma variável de iteração cujo valor é determinado por uma expressão em vez de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="e09d3-141">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="e09d3-142">Use o `Distinct` cláusula para ignorar os resultados da consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="e09d3-142">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="e09d3-143">Identificar partes do que o resultado retornar usando o `Skip`, `Take`, `Skip While`, e `Take While` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="e09d3-143">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e09d3-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e09d3-144">Example</span></span>  
 <span data-ttu-id="e09d3-145">A seguinte consulta expressão utiliza um `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção.</span><span class="sxs-lookup"><span data-stu-id="e09d3-145">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e09d3-146">O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada.</span><span class="sxs-lookup"><span data-stu-id="e09d3-146">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e09d3-147">O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="e09d3-147">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 <span data-ttu-id="e09d3-148">[!code-vb[VbSimpleQuerySamples&#23;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e09d3-148">[!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09d3-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e09d3-149">See Also</span></span>  
 <span data-ttu-id="e09d3-150">[Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-150">[Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="e09d3-151"> [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-151"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="e09d3-152"> [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-152"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="e09d3-153"> [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-153"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="e09d3-154"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-154"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="e09d3-155"> [Onde cláusula](../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-155"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="e09d3-156"> [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-156"> [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="e09d3-157"> [Cláusula DISTINCT](../../../visual-basic/language-reference/queries/distinct-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-157"> [Distinct Clause](../../../visual-basic/language-reference/queries/distinct-clause.md) </span></span>  
<span data-ttu-id="e09d3-158"> [Cláusula JOIN](../../../visual-basic/language-reference/queries/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-158"> [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md) </span></span>  
<span data-ttu-id="e09d3-159"> [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-159"> [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md) </span></span>  
<span data-ttu-id="e09d3-160"> [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-160"> [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="e09d3-161"> [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-161"> [Let Clause](../../../visual-basic/language-reference/queries/let-clause.md) </span></span>  
<span data-ttu-id="e09d3-162"> [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-162"> [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md) </span></span>  
<span data-ttu-id="e09d3-163"> [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-163"> [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md) </span></span>  
<span data-ttu-id="e09d3-164"> [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e09d3-164"> [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) </span></span>  
<span data-ttu-id="e09d3-165"> [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)</span><span class="sxs-lookup"><span data-stu-id="e09d3-165"> [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)</span></span>
