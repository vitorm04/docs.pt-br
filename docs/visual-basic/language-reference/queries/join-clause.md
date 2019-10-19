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
ms.openlocfilehash: b5211d0ed3f618013dc9fe764a6d7b2db8177c26
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582288"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="71059-102">Cláusula Join (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71059-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="71059-103">Combina duas coleções em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="71059-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="71059-104">A operação de junção é baseada em chaves correspondentes e usa o operador de `Equals`.</span><span class="sxs-lookup"><span data-stu-id="71059-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="71059-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71059-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="71059-106">Partes</span><span class="sxs-lookup"><span data-stu-id="71059-106">Parts</span></span>

<span data-ttu-id="71059-107">`element` Necessário.</span><span class="sxs-lookup"><span data-stu-id="71059-107">`element` Required.</span></span> <span data-ttu-id="71059-108">A variável de controle para a coleção que está sendo unida.</span><span class="sxs-lookup"><span data-stu-id="71059-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="71059-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="71059-109">Required.</span></span> <span data-ttu-id="71059-110">A coleção a ser combinada com a coleção identificada no lado esquerdo do operador de `Join`.</span><span class="sxs-lookup"><span data-stu-id="71059-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="71059-111">Uma cláusula `Join` pode ser aninhada em outra cláusula `Join` ou em uma cláusula `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="71059-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="71059-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="71059-112">Optional.</span></span> <span data-ttu-id="71059-113">Uma ou mais cláusulas de `Join` adicionais para refinar ainda mais a consulta.</span><span class="sxs-lookup"><span data-stu-id="71059-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="71059-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="71059-114">Optional.</span></span> <span data-ttu-id="71059-115">Uma ou mais cláusulas de `Group Join` adicionais para refinar ainda mais a consulta.</span><span class="sxs-lookup"><span data-stu-id="71059-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="71059-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="71059-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="71059-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="71059-117">Required.</span></span> <span data-ttu-id="71059-118">Identifica as chaves para as coleções que estão sendo Unidas.</span><span class="sxs-lookup"><span data-stu-id="71059-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="71059-119">Você deve usar o operador de `Equals` para comparar as chaves das coleções que estão sendo Unidas.</span><span class="sxs-lookup"><span data-stu-id="71059-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="71059-120">Você pode combinar condições de junção usando o operador de `And` para identificar várias chaves.</span><span class="sxs-lookup"><span data-stu-id="71059-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="71059-121">`key1` deve ser da coleção no lado esquerdo do operador de `Join`.</span><span class="sxs-lookup"><span data-stu-id="71059-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="71059-122">`key2` deve ser da coleção no lado direito do operador de `Join`.</span><span class="sxs-lookup"><span data-stu-id="71059-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="71059-123">As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção.</span><span class="sxs-lookup"><span data-stu-id="71059-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="71059-124">No entanto, cada expressão de chave pode conter apenas itens de sua respectiva coleção.</span><span class="sxs-lookup"><span data-stu-id="71059-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="71059-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="71059-125">Remarks</span></span>

<span data-ttu-id="71059-126">A cláusula `Join` combina duas coleções com base nos valores de chave correspondentes das coleções que estão sendo Unidas.</span><span class="sxs-lookup"><span data-stu-id="71059-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="71059-127">A coleção resultante pode conter qualquer combinação de valores da coleção identificada no lado esquerdo do operador de `Join` e da coleção identificada na cláusula `Join`.</span><span class="sxs-lookup"><span data-stu-id="71059-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="71059-128">A consulta retornará apenas resultados para os quais a condição especificada pelo operador de `Equals` é atendida.</span><span class="sxs-lookup"><span data-stu-id="71059-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="71059-129">Isso é equivalente a um `INNER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="71059-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="71059-130">Você pode usar várias cláusulas `Join` em uma consulta para unir duas ou mais coleções em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="71059-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="71059-131">Você pode executar uma junção implícita para combinar coleções sem a cláusula `Join`.</span><span class="sxs-lookup"><span data-stu-id="71059-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="71059-132">Para fazer isso, inclua várias cláusulas `In` na cláusula `From` e especifique uma cláusula `Where` que identifique as chaves que você deseja usar para a junção.</span><span class="sxs-lookup"><span data-stu-id="71059-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="71059-133">Você pode usar a cláusula `Group Join` para combinar coleções em uma única coleção hierárquica.</span><span class="sxs-lookup"><span data-stu-id="71059-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="71059-134">Isso é como uma `LEFT OUTER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="71059-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="71059-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71059-135">Example</span></span>

<span data-ttu-id="71059-136">O exemplo de código a seguir executa uma junção implícita para combinar uma lista de clientes com seus pedidos.</span><span class="sxs-lookup"><span data-stu-id="71059-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="71059-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71059-137">Example</span></span>

<span data-ttu-id="71059-138">O exemplo de código a seguir une duas coleções usando a cláusula `Join`.</span><span class="sxs-lookup"><span data-stu-id="71059-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="71059-139">Este exemplo produzirá uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="71059-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="71059-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71059-140">Example</span></span>

<span data-ttu-id="71059-141">O exemplo de código a seguir une duas coleções usando a cláusula `Join` com duas colunas de chave.</span><span class="sxs-lookup"><span data-stu-id="71059-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="71059-142">O exemplo produzirá uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="71059-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="71059-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71059-143">See also</span></span>

- [<span data-ttu-id="71059-144">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71059-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="71059-145">Consultas</span><span class="sxs-lookup"><span data-stu-id="71059-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="71059-146">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="71059-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="71059-147">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="71059-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="71059-148">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="71059-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="71059-149">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="71059-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
