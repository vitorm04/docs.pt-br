---
title: "Cláusula JOIN (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement
- Join clause
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
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
ms.openlocfilehash: a4cef9cf1e025809eac963acf8c08288ea5fde6f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="44367-102">Cláusula Join (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44367-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="44367-103">Combina duas coleções em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="44367-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="44367-104">A operação de junção é baseada em chaves correspondentes e usa o `Equals` operador.</span><span class="sxs-lookup"><span data-stu-id="44367-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44367-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44367-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="44367-106">Partes</span><span class="sxs-lookup"><span data-stu-id="44367-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="44367-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="44367-107">Required.</span></span> <span data-ttu-id="44367-108">A variável de controle para a coleção sendo associada.</span><span class="sxs-lookup"><span data-stu-id="44367-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="44367-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="44367-109">Required.</span></span> <span data-ttu-id="44367-110">A coleção a combinar com a coleção identificada no lado esquerdo do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="44367-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="44367-111">A `Join` cláusula pode ser aninhada em outro `Join` cláusula, ou em um `Group Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44367-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="44367-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="44367-112">Optional.</span></span> <span data-ttu-id="44367-113">Um ou mais adicionais `Join` outras cláusulas refinar a consulta.</span><span class="sxs-lookup"><span data-stu-id="44367-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="44367-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="44367-114">Optional.</span></span> <span data-ttu-id="44367-115">Um ou mais adicionais `Group Join` outras cláusulas refinar a consulta.</span><span class="sxs-lookup"><span data-stu-id="44367-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="44367-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="44367-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="44367-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="44367-117">Required.</span></span> <span data-ttu-id="44367-118">Identifica chaves para as coleções que estão sendo combinadas.</span><span class="sxs-lookup"><span data-stu-id="44367-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="44367-119">Você deve usar o `Equals` operador para comparar chaves das coleções que estão sendo combinadas.</span><span class="sxs-lookup"><span data-stu-id="44367-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="44367-120">Você pode combinar condições de associação usando o `And` operador para identificar várias chaves.</span><span class="sxs-lookup"><span data-stu-id="44367-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="44367-121">`key1`deve ser da coleção no lado esquerdo do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="44367-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="44367-122">`key2`deve ser da coleção no lado direito do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="44367-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="44367-123">As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção.</span><span class="sxs-lookup"><span data-stu-id="44367-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="44367-124">No entanto, cada expressão chave pode conter somente itens da sua respectiva coleção.</span><span class="sxs-lookup"><span data-stu-id="44367-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44367-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="44367-125">Remarks</span></span>  
 <span data-ttu-id="44367-126">O `Join` cláusula combina duas coleções baseadas nos valores de chave das coleções que estão sendo combinadas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="44367-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="44367-127">A coleção resultante pode conter qualquer combinação de valores da coleção no lado esquerdo do `Join` operador e na coleção identificada no `Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44367-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="44367-128">A consulta retornará apenas os resultados para os quais a condição especificada, o `Equals` operador for atendido.</span><span class="sxs-lookup"><span data-stu-id="44367-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="44367-129">Isso é equivalente a um `INNER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="44367-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="44367-130">Você pode usar várias `Join` cláusulas em uma consulta para unir dois ou mais coleções em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="44367-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="44367-131">Você pode executar uma junção implícita para combinar coleções sem a `Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44367-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="44367-132">Para fazer isso, incluir vários `In` cláusulas em seu `From` cláusula e especifique um `Where` cláusula que identifica as chaves que você deseja usar para a junção.</span><span class="sxs-lookup"><span data-stu-id="44367-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="44367-133">Você pode usar o `Group Join` cláusula para combinar coleções em uma única coleção hierárquica.</span><span class="sxs-lookup"><span data-stu-id="44367-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="44367-134">Isso é como um `LEFT OUTER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="44367-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44367-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44367-135">Example</span></span>  
 <span data-ttu-id="44367-136">O exemplo de código a seguir executa uma junção implícita para combinar uma lista de clientes com seus pedidos.</span><span class="sxs-lookup"><span data-stu-id="44367-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 <span data-ttu-id="44367-137">[!code-vb[VbSimpleQuerySamples&13;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="44367-137">[!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="44367-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44367-138">Example</span></span>  
 <span data-ttu-id="44367-139">O exemplo de código a seguir une duas coleções usando a `Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44367-139">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="44367-140">[!code-vb[VbSimpleQuerySamples&#12;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="44367-140">[!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]</span></span>  
  
 <span data-ttu-id="44367-141">Este exemplo produzirá a saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="44367-141">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="44367-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44367-142">Example</span></span>  
 <span data-ttu-id="44367-143">O exemplo de código a seguir une duas coleções usando a `Join` cláusula com duas colunas de chave.</span><span class="sxs-lookup"><span data-stu-id="44367-143">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 <span data-ttu-id="44367-144">[!code-vb[17 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="44367-144">[!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]</span></span>  
  
 <span data-ttu-id="44367-145">Este exemplo produzirá a saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="44367-145">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="44367-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44367-146">See Also</span></span>  
 <span data-ttu-id="44367-147">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="44367-147">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="44367-148"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="44367-148"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="44367-149"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="44367-149"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="44367-150"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="44367-150"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="44367-151"> [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="44367-151"> [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md) </span></span>  
<span data-ttu-id="44367-152"> [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="44367-152"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)</span></span>
