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
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396175"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="15386-102">Cláusula From (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15386-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="15386-103">Especifica uma ou mais variáveis de intervalo e uma coleção a ser consultada.</span><span class="sxs-lookup"><span data-stu-id="15386-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15386-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15386-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="15386-105">Partes</span><span class="sxs-lookup"><span data-stu-id="15386-105">Parts</span></span>  
  
|<span data-ttu-id="15386-106">Termo</span><span class="sxs-lookup"><span data-stu-id="15386-106">Term</span></span>|<span data-ttu-id="15386-107">Definição</span><span class="sxs-lookup"><span data-stu-id="15386-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="15386-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="15386-108">Required.</span></span> <span data-ttu-id="15386-109">Uma *variável de intervalo* usada para iterar pelos elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="15386-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="15386-110">Uma variável de intervalo é usada para fazer referência a cada membro do `collection` à medida que a consulta é iterada por meio do `collection` .</span><span class="sxs-lookup"><span data-stu-id="15386-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="15386-111">Deve ser um tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="15386-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="15386-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="15386-112">Optional.</span></span> <span data-ttu-id="15386-113">O tipo de `element`.</span><span class="sxs-lookup"><span data-stu-id="15386-113">The type of `element`.</span></span> <span data-ttu-id="15386-114">Se não `type` for especificado, o tipo de `element` será inferido de `collection` .</span><span class="sxs-lookup"><span data-stu-id="15386-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="15386-115">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="15386-115">Required.</span></span> <span data-ttu-id="15386-116">Refere-se à coleção a ser consultada.</span><span class="sxs-lookup"><span data-stu-id="15386-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="15386-117">Deve ser um tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="15386-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15386-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="15386-118">Remarks</span></span>  
 <span data-ttu-id="15386-119">A `From` cláusula é usada para identificar os dados de origem de uma consulta e as variáveis que são usadas para fazer referência a um elemento da coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="15386-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="15386-120">Essas variáveis são chamadas de *variáveis de intervalo*.</span><span class="sxs-lookup"><span data-stu-id="15386-120">These variables are called *range variables*.</span></span> <span data-ttu-id="15386-121">A `From` cláusula é necessária para uma consulta, exceto quando a `Aggregate` cláusula é usada para identificar uma consulta que retorna apenas resultados agregados.</span><span class="sxs-lookup"><span data-stu-id="15386-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="15386-122">Para obter mais informações, consulte [cláusula Aggregate](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="15386-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="15386-123">Você pode especificar várias `From` cláusulas em uma consulta para identificar várias coleções a serem unidas.</span><span class="sxs-lookup"><span data-stu-id="15386-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="15386-124">Quando várias coleções são especificadas, elas são iteradas de forma independente ou você pode associá-las se estiverem relacionadas.</span><span class="sxs-lookup"><span data-stu-id="15386-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="15386-125">Você pode unir coleções implicitamente usando a `Select` cláusula ou explicitamente usando as `Join` `Group Join` cláusulas ou.</span><span class="sxs-lookup"><span data-stu-id="15386-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="15386-126">Como alternativa, você pode especificar várias variáveis de intervalo e coleções em uma única `From` cláusula, com cada variável de intervalo relacionada e uma coleção separada das outras por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="15386-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="15386-127">O exemplo de código a seguir mostra ambas as opções de sintaxe para a `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="15386-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="15386-128">A `From` cláusula define o escopo de uma consulta, que é semelhante ao escopo de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="15386-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="15386-129">Portanto, cada `element` variável de intervalo no escopo de uma consulta deve ter um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="15386-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="15386-130">Como você pode especificar várias `From` cláusulas para uma consulta, as `From` cláusulas subsequentes podem se referir a variáveis de intervalo na `From` cláusula, ou podem se referir a variáveis de intervalo em uma `From` cláusula anterior.</span><span class="sxs-lookup"><span data-stu-id="15386-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="15386-131">Por exemplo, o exemplo a seguir mostra uma `From` cláusula aninhada onde a coleção na segunda cláusula é baseada em uma propriedade da variável Range na primeira cláusula.</span><span class="sxs-lookup"><span data-stu-id="15386-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="15386-132">Cada `From` cláusula pode ser seguida por qualquer combinação de cláusulas de consulta adicionais para refinar a consulta.</span><span class="sxs-lookup"><span data-stu-id="15386-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="15386-133">Você pode refinar a consulta das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="15386-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="15386-134">Combine várias coleções implicitamente usando as `From` `Select` cláusulas e, ou explicitamente, usando as `Join` `Group Join` cláusulas ou.</span><span class="sxs-lookup"><span data-stu-id="15386-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="15386-135">Use a `Where` cláusula para filtrar o resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="15386-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="15386-136">Classifique o resultado usando a `Order By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="15386-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="15386-137">Agrupe resultados semelhantes em conjunto usando a `Group By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="15386-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="15386-138">Use a `Aggregate` cláusula para identificar funções de agregação a serem avaliadas para todo o resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="15386-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="15386-139">Use a `Let` cláusula para introduzir uma variável de iteração cujo valor é determinado por uma expressão em vez de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="15386-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="15386-140">Use a `Distinct` cláusula para ignorar os resultados de consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="15386-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="15386-141">Identifique partes do resultado a serem retornadas usando as `Skip` `Take` `Skip While` cláusulas,, e `Take While` .</span><span class="sxs-lookup"><span data-stu-id="15386-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15386-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15386-142">Example</span></span>  
 <span data-ttu-id="15386-143">A expressão de consulta a seguir usa uma `From` cláusula para declarar uma variável `cust` de intervalo para cada `Customer` objeto na `customers` coleção.</span><span class="sxs-lookup"><span data-stu-id="15386-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="15386-144">A `Where` cláusula usa a variável Range para restringir a saída aos clientes da região especificada.</span><span class="sxs-lookup"><span data-stu-id="15386-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="15386-145">O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="15386-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="15386-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="15386-146">See also</span></span>

- [<span data-ttu-id="15386-147">Consultas</span><span class="sxs-lookup"><span data-stu-id="15386-147">Queries</span></span>](index.md)
- [<span data-ttu-id="15386-148">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15386-148">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="15386-149">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="15386-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="15386-150">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="15386-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="15386-151">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="15386-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="15386-152">Cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="15386-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="15386-153">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="15386-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="15386-154">Cláusula Distinct</span><span class="sxs-lookup"><span data-stu-id="15386-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="15386-155">Cláusula JOIN</span><span class="sxs-lookup"><span data-stu-id="15386-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="15386-156">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="15386-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="15386-157">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="15386-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="15386-158">Cláusula Let</span><span class="sxs-lookup"><span data-stu-id="15386-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="15386-159">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="15386-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="15386-160">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="15386-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="15386-161">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="15386-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="15386-162">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="15386-162">Take While Clause</span></span>](take-while-clause.md)
