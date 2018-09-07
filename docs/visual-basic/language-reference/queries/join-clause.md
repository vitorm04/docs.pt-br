---
title: Cláusula Join (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: b1551583079c66d1bf5f6963a42d5d24e518fff3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066254"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="e111a-102">Cláusula Join (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e111a-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="e111a-103">Combina duas coleções em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="e111a-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="e111a-104">A operação de junção é baseada em chaves correspondentes e usa o `Equals` operador.</span><span class="sxs-lookup"><span data-stu-id="e111a-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e111a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e111a-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e111a-106">Partes</span><span class="sxs-lookup"><span data-stu-id="e111a-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="e111a-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e111a-107">Required.</span></span> <span data-ttu-id="e111a-108">A variável de controle para a coleção sendo unida.</span><span class="sxs-lookup"><span data-stu-id="e111a-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="e111a-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e111a-109">Required.</span></span> <span data-ttu-id="e111a-110">A coleção a combinar com a coleção identificada no lado esquerdo do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="e111a-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="e111a-111">Um `Join` cláusula pode ser aninhada em outro `Join` cláusula, ou em um `Group Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e111a-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="e111a-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e111a-112">Optional.</span></span> <span data-ttu-id="e111a-113">Um ou mais adicionais `Join` cláusulas ainda mais a refinar a consulta.</span><span class="sxs-lookup"><span data-stu-id="e111a-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="e111a-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e111a-114">Optional.</span></span> <span data-ttu-id="e111a-115">Um ou mais adicionais `Group Join` cláusulas ainda mais a refinar a consulta.</span><span class="sxs-lookup"><span data-stu-id="e111a-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="e111a-116">`key1``Equals``key2`</span><span class="sxs-lookup"><span data-stu-id="e111a-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="e111a-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e111a-117">Required.</span></span> <span data-ttu-id="e111a-118">Identifica as chaves para as coleções que estão sendo unidas.</span><span class="sxs-lookup"><span data-stu-id="e111a-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="e111a-119">Você deve usar o `Equals` operador para comparar as chaves das coleções que estão sendo combinadas.</span><span class="sxs-lookup"><span data-stu-id="e111a-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="e111a-120">Você pode combinar condições de junção, usando o `And` operador para identificar várias chaves.</span><span class="sxs-lookup"><span data-stu-id="e111a-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="e111a-121">`key1` deve ser da coleção no lado esquerdo do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="e111a-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="e111a-122">`key2` deve ser da coleção no lado direito do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="e111a-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="e111a-123">As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção.</span><span class="sxs-lookup"><span data-stu-id="e111a-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="e111a-124">No entanto, cada expressão de chave pode conter apenas os itens de sua respectiva coleção.</span><span class="sxs-lookup"><span data-stu-id="e111a-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e111a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="e111a-125">Remarks</span></span>  
 <span data-ttu-id="e111a-126">O `Join` cláusula combina duas coleções com base na correspondência de valores de chave das coleções que estão sendo combinadas.</span><span class="sxs-lookup"><span data-stu-id="e111a-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="e111a-127">A coleção resultante pode conter qualquer combinação de valores da coleção no lado esquerdo dos `Join` operador e na coleção identificada no `Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e111a-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="e111a-128">A consulta retornará apenas os resultados para os quais a condição especificada pelo `Equals` operador for atendido.</span><span class="sxs-lookup"><span data-stu-id="e111a-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="e111a-129">Isso é equivalente a um `INNER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="e111a-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="e111a-130">Você pode usar várias `Join` cláusulas em uma consulta para unir duas ou mais coleções em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="e111a-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="e111a-131">Você pode executar uma junção implícita para combinar coleções sem o `Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e111a-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="e111a-132">Para fazer isso, incluir vários `In` cláusulas em seu `From` cláusula e especifique um `Where` cláusula que identifica as chaves que você deseja usar para a junção.</span><span class="sxs-lookup"><span data-stu-id="e111a-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="e111a-133">Você pode usar o `Group Join` cláusula para combinar coleções em uma única coleção hierárquica.</span><span class="sxs-lookup"><span data-stu-id="e111a-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="e111a-134">Isso é como um `LEFT OUTER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="e111a-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e111a-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e111a-135">Example</span></span>  
 <span data-ttu-id="e111a-136">O exemplo de código a seguir executa uma junção implícita para combinar uma lista de clientes com seus pedidos.</span><span class="sxs-lookup"><span data-stu-id="e111a-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e111a-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e111a-137">Example</span></span>  
 <span data-ttu-id="e111a-138">O exemplo de código a seguir une duas coleções usando o `Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e111a-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 <span data-ttu-id="e111a-139">Este exemplo produzirá saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="e111a-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="e111a-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e111a-140">Example</span></span>  
 <span data-ttu-id="e111a-141">O exemplo de código a seguir une duas coleções usando o `Join` cláusula com duas colunas de chave.</span><span class="sxs-lookup"><span data-stu-id="e111a-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 <span data-ttu-id="e111a-142">O exemplo produzirá saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="e111a-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="e111a-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e111a-143">See Also</span></span>  
 [<span data-ttu-id="e111a-144">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e111a-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="e111a-145">Consultas</span><span class="sxs-lookup"><span data-stu-id="e111a-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="e111a-146">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="e111a-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="e111a-147">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="e111a-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="e111a-148">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="e111a-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="e111a-149">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="e111a-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
