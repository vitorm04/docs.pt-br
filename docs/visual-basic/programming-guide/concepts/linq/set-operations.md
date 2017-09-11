---
title: "Definir operações (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
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
ms.openlocfilehash: 2b9fd7ec122fff2601296ae3a46bb7607b2b32ef
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="bb263-102">Operações de conjunto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb263-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="bb263-103">Operações de conjunto em LINQ, consulte operações de consulta que produzem um conjunto de resultados com base na presença ou ausência de elementos equivalentes dentro do mesmo ou separados coleções (ou conjuntos).</span><span class="sxs-lookup"><span data-stu-id="bb263-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="bb263-104">Os métodos de operador de consulta padrão que realizam operações de conjunto são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb263-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb263-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="bb263-105">Methods</span></span>  
  
|<span data-ttu-id="bb263-106">Nome do método</span><span class="sxs-lookup"><span data-stu-id="bb263-106">Method Name</span></span>|<span data-ttu-id="bb263-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb263-107">Description</span></span>|<span data-ttu-id="bb263-108">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb263-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="bb263-109">Mais informações</span><span class="sxs-lookup"><span data-stu-id="bb263-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="bb263-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="bb263-110">Distinct</span></span>|<span data-ttu-id="bb263-111">Remove os valores de uma coleção duplicados.</span><span class="sxs-lookup"><span data-stu-id="bb263-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<span data-ttu-id="bb263-112"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-112"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="bb263-113"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-113"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="bb263-114">Exceto</span><span class="sxs-lookup"><span data-stu-id="bb263-114">Except</span></span>|<span data-ttu-id="bb263-115">Retorna a diferença de conjunto, o que significa que os elementos de uma coleção que não aparecem em uma segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="bb263-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="bb263-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="bb263-116">Not applicable.</span></span>|<span data-ttu-id="bb263-117"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-117"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="bb263-118"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-118"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="bb263-119">Interseção</span><span class="sxs-lookup"><span data-stu-id="bb263-119">Intersect</span></span>|<span data-ttu-id="bb263-120">Retorna a interseção de conjunto, o que significa que os elementos que aparecem em cada uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="bb263-120">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="bb263-121">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="bb263-121">Not applicable.</span></span>|<span data-ttu-id="bb263-122"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-122"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="bb263-123"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-123"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="bb263-124">União</span><span class="sxs-lookup"><span data-stu-id="bb263-124">Union</span></span>|<span data-ttu-id="bb263-125">Retorna a união de conjunto, o que significa que os elementos exclusivos que aparecem em qualquer uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="bb263-125">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="bb263-126">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="bb263-126">Not applicable.</span></span>|<span data-ttu-id="bb263-127"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-127"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="bb263-128"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-128"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span></span>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="bb263-129">Comparação de operações de conjunto</span><span class="sxs-lookup"><span data-stu-id="bb263-129">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="bb263-130">Distinct</span><span class="sxs-lookup"><span data-stu-id="bb263-130">Distinct</span></span>  
 <span data-ttu-id="bb263-131">A ilustração a seguir descreve o comportamento do <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>método em uma sequência de caracteres.</xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-131">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> method on a sequence of characters.</span></span> <span data-ttu-id="bb263-132">A sequência retornada contém os elementos exclusivos da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="bb263-132">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="bb263-133">![Gráfico mostrando o comportamento de Distinct(). ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distintos")</span><span class="sxs-lookup"><span data-stu-id="bb263-133">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="bb263-134">Exceto</span><span class="sxs-lookup"><span data-stu-id="bb263-134">Except</span></span>  
 <span data-ttu-id="bb263-135">A ilustração a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-135">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="bb263-136">A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="bb263-136">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="bb263-137">![Gráfico mostrando a ação de EXCEPT (). ](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="bb263-137">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="bb263-138">Interseção</span><span class="sxs-lookup"><span data-stu-id="bb263-138">Intersect</span></span>  
 <span data-ttu-id="bb263-139">A ilustração a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb263-139">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="bb263-140">A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.</span><span class="sxs-lookup"><span data-stu-id="bb263-140">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="bb263-141">![Gráfico mostrando a interseção de duas sequências. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="bb263-141">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="bb263-142">União</span><span class="sxs-lookup"><span data-stu-id="bb263-142">Union</span></span>  
 <span data-ttu-id="bb263-143">A ilustração a seguir mostra uma operação de união em duas sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bb263-143">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="bb263-144">A sequência retornada contém os elementos exclusivos de ambas as sequências.</span><span class="sxs-lookup"><span data-stu-id="bb263-144">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="bb263-145">![Gráfico mostrando a união de duas sequências. ](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="bb263-145">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="bb263-146">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="bb263-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="bb263-147">O exemplo a seguir usa o `Distinct` cláusula em uma consulta LINQ para retornar os números exclusivos de uma lista de números inteiros.</span><span class="sxs-lookup"><span data-stu-id="bb263-147">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 <span data-ttu-id="bb263-148">[!code-vb[CsLINQSetOps n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bb263-148">[!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb263-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb263-149">See Also</span></span>  
 <span data-ttu-id="bb263-150"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="bb263-150"><xref:System.Linq></span></span>   
<span data-ttu-id="bb263-151"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="bb263-151"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="bb263-152"> [Cláusula DISTINCT](../../../../visual-basic/language-reference/queries/distinct-clause.md) </span><span class="sxs-lookup"><span data-stu-id="bb263-152"> [Distinct Clause](../../../../visual-basic/language-reference/queries/distinct-clause.md) </span></span>  
<span data-ttu-id="bb263-153"> [Como: combinar e comparar coleções de cadeia de caracteres (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span><span class="sxs-lookup"><span data-stu-id="bb263-153"> [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span></span>  
<span data-ttu-id="bb263-154"> [Como: localizar a diferença definida entre as duas listas (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span><span class="sxs-lookup"><span data-stu-id="bb263-154"> [How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span></span>
