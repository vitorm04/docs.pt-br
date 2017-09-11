---
title: "Cláusula Join (Visual Basic) de grupo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
dev_langs:
- VB
helpviewer_keywords:
- Group Join clause
- Group Join statement
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: 24
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
ms.openlocfilehash: 44310b9250bbd9b697b189c5bc1f9ccbb45a5344
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="5d4d2-102">Cláusula Join Group (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d4d2-102">Group Join Clause (Visual Basic)</span></span>
<span data-ttu-id="5d4d2-103">Combina duas coleções em uma única coleção hierárquica.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-103">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="5d4d2-104">A operação de junção é baseada em chaves correspondentes.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-104">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d4d2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d4d2-105">Syntax</span></span>  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="5d4d2-106">Partes</span><span class="sxs-lookup"><span data-stu-id="5d4d2-106">Parts</span></span>  
  
|<span data-ttu-id="5d4d2-107">Termo</span><span class="sxs-lookup"><span data-stu-id="5d4d2-107">Term</span></span>|<span data-ttu-id="5d4d2-108">Definição</span><span class="sxs-lookup"><span data-stu-id="5d4d2-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="5d4d2-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-109">Required.</span></span> <span data-ttu-id="5d4d2-110">A variável de controle para a coleção sendo associada.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-110">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="5d4d2-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-111">Optional.</span></span> <span data-ttu-id="5d4d2-112">O tipo de `element`.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-112">The type of `element`.</span></span> <span data-ttu-id="5d4d2-113">Se nenhum `type` for especificado, o tipo de `element` é inferido do `collection`.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-113">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="5d4d2-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-114">Required.</span></span> <span data-ttu-id="5d4d2-115">A coleção a combinar com a coleção que está no lado esquerdo do `Group Join` operador.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-115">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="5d4d2-116">A `Group Join` cláusula pode ser aninhada em uma `Join` cláusula ou em outro `Group Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-116">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="5d4d2-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="5d4d2-117">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="5d4d2-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-118">Required.</span></span> <span data-ttu-id="5d4d2-119">Identifica chaves para as coleções que estão sendo combinadas.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="5d4d2-120">Você deve usar o `Equals` operador para comparar chaves das coleções que estão sendo combinadas.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="5d4d2-121">Você pode combinar condições de associação usando o `And` operador para identificar várias chaves.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="5d4d2-122">O `key1` parâmetro deve ser da coleção no lado esquerdo do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-122">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="5d4d2-123">O `key2` parâmetro deve ser da coleção no lado direito do `Join` operador.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-123">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="5d4d2-124">As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="5d4d2-125">No entanto, cada expressão chave pode conter somente itens da sua respectiva coleção.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-125">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="5d4d2-126">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-126">Required.</span></span> <span data-ttu-id="5d4d2-127">Uma ou mais expressões que identificam como os grupos de elementos da coleção são agregados.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-127">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="5d4d2-128">Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave (`<alias> = Group`).</span><span class="sxs-lookup"><span data-stu-id="5d4d2-128">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="5d4d2-129">Você também pode incluir funções agregadas para aplicar ao grupo.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-129">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d4d2-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d4d2-130">Remarks</span></span>  
 <span data-ttu-id="5d4d2-131">O `Group Join` cláusula combina duas coleções baseadas nos valores de chave das coleções que estão sendo combinadas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-131">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="5d4d2-132">A coleção resultante pode conter um membro que referencia uma coleção de elementos da segunda coleção que corresponde ao valor de chave da coleção primeiro.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-132">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="5d4d2-133">Você também pode especificar funções agregadas para aplicar aos elementos agrupados da segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-133">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="5d4d2-134">Para obter informações sobre funções de agregação, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5d4d2-134">For information about aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="5d4d2-135">Considere, por exemplo, uma coleção de gerentes e uma coleção de funcionários.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-135">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="5d4d2-136">Elementos de ambos os conjuntos possuem uma propriedade ManagerID que identifica os funcionários subordinados a um gerente específico.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-136">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="5d4d2-137">Os resultados de uma operação de junção conterá um resultado para cada gerente e funcionário com um valor coincidente ManagerID.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-137">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="5d4d2-138">Os resultados de uma `Group Join` operação contém a lista completa dos gerentes.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-138">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="5d4d2-139">Cada gerente no resultado teria um membro a lista de funcionários que eram uma correspondência para o gerente específico.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-139">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="5d4d2-140">O conjunto resultante de uma `Group Join` operação pode conter qualquer combinação de valores de coleção identificados no `From` cláusula e as expressões identificadas no `Into` cláusula do `Group Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-140">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="5d4d2-141">Para obter mais informações sobre expressões válidas para a `Into` cláusula, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5d4d2-141">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="5d4d2-142">A `Group Join` operação retornará todos os resultados da coleção identificada no lado esquerdo do `Group Join` operador.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-142">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="5d4d2-143">Isso é verdadeiro mesmo se não houver nenhuma correspondência na coleção sendo associado.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-143">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="5d4d2-144">Isso é como um `LEFT OUTER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-144">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="5d4d2-145">Você pode usar o `Join` cláusula para combinar coleções em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-145">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="5d4d2-146">Isso é equivalente a um `INNER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-146">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d4d2-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d4d2-147">Example</span></span>  
 <span data-ttu-id="5d4d2-148">O exemplo de código a seguir une duas coleções usando a `Group Join` cláusula.</span><span class="sxs-lookup"><span data-stu-id="5d4d2-148">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 <span data-ttu-id="5d4d2-149">[!code-vb[VbSimpleQuerySamples&#14;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5d4d2-149">[!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4d2-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d4d2-150">See Also</span></span>  
 <span data-ttu-id="5d4d2-151">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="5d4d2-151">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="5d4d2-152"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="5d4d2-152"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="5d4d2-153"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="5d4d2-153"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="5d4d2-154"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="5d4d2-154"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="5d4d2-155"> [Cláusula JOIN](../../../visual-basic/language-reference/queries/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="5d4d2-155"> [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md) </span></span>  
<span data-ttu-id="5d4d2-156"> [Onde cláusula](../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="5d4d2-156"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="5d4d2-157"> [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)</span><span class="sxs-lookup"><span data-stu-id="5d4d2-157"> [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md)</span></span>
