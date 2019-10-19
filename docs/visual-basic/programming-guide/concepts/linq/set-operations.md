---
title: Operações Set (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: fe8dbff00ecd6da9b3b0e9792e67422583a00180
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582918"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="c7e58-102">Operações Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e58-102">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="c7e58-103">As operações de conjunto na LINQ referem-se a operações de consulta que geram um conjunto de resultados baseado na presença ou ausência de elementos equivalentes dentro da mesma ou de coleções (ou conjuntos) separadas.</span><span class="sxs-lookup"><span data-stu-id="c7e58-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="c7e58-104">Os métodos de operador de consulta padrão que executam operações de conjunto estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7e58-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="c7e58-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7e58-105">Methods</span></span>

|<span data-ttu-id="c7e58-106">Nome do método</span><span class="sxs-lookup"><span data-stu-id="c7e58-106">Method Name</span></span>|<span data-ttu-id="c7e58-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7e58-107">Description</span></span>|<span data-ttu-id="c7e58-108">Visual Basic sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="c7e58-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c7e58-109">Mais informações</span><span class="sxs-lookup"><span data-stu-id="c7e58-109">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="c7e58-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="c7e58-110">Distinct</span></span>|<span data-ttu-id="c7e58-111">Remove os valores duplicados de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="c7e58-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c7e58-112">Exceto</span><span class="sxs-lookup"><span data-stu-id="c7e58-112">Except</span></span>|<span data-ttu-id="c7e58-113">Retorna a diferença de conjunto, que significa os elementos de uma coleção que não aparecem em uma segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="c7e58-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="c7e58-114">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="c7e58-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c7e58-115">Interseção</span><span class="sxs-lookup"><span data-stu-id="c7e58-115">Intersect</span></span>|<span data-ttu-id="c7e58-116">Retorna a interseção de conjunto, o que significa os elementos que aparecem em cada uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="c7e58-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="c7e58-117">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="c7e58-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c7e58-118">União</span><span class="sxs-lookup"><span data-stu-id="c7e58-118">Union</span></span>|<span data-ttu-id="c7e58-119">Retorna a união de conjunto, o que significa os elementos únicos que aparecem em qualquer uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="c7e58-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="c7e58-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="c7e58-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="c7e58-121">Comparação de operações de conjuntos</span><span class="sxs-lookup"><span data-stu-id="c7e58-121">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="c7e58-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="c7e58-122">Distinct</span></span>

<span data-ttu-id="c7e58-123">A ilustração a seguir mostra o comportamento do método <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c7e58-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="c7e58-124">A sequência retornada contém os elementos exclusivos da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="c7e58-124">The returned sequence contains the unique elements from the input sequence.</span></span>

![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="c7e58-126">Exceto</span><span class="sxs-lookup"><span data-stu-id="c7e58-126">Except</span></span>

<span data-ttu-id="c7e58-127">A ilustração a seguir mostra o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7e58-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c7e58-128">A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="c7e58-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="c7e58-129">![Gráfico mostrando a ação de Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Mostra o comportamento de Except.")</span><span class="sxs-lookup"><span data-stu-id="c7e58-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="c7e58-130">Interseção</span><span class="sxs-lookup"><span data-stu-id="c7e58-130">Intersect</span></span>

<span data-ttu-id="c7e58-131">A ilustração a seguir mostra o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7e58-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c7e58-132">A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.</span><span class="sxs-lookup"><span data-stu-id="c7e58-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![Gráfico mostrando a interseção de duas sequências.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="c7e58-134">União</span><span class="sxs-lookup"><span data-stu-id="c7e58-134">Union</span></span>

<span data-ttu-id="c7e58-135">A ilustração a seguir descreve uma operação de união em duas sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c7e58-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="c7e58-136">A sequência retornada contém os elementos exclusivos das duas sequências de entrada.</span><span class="sxs-lookup"><span data-stu-id="c7e58-136">The returned sequence contains the unique elements from both input sequences.</span></span>

![Gráfico mostrando a união de duas sequências.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="c7e58-138">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="c7e58-138">Query Expression Syntax Example</span></span>

<span data-ttu-id="c7e58-139">O exemplo a seguir usa a cláusula `Distinct` em uma consulta LINQ para retornar os números exclusivos de uma lista de inteiros.</span><span class="sxs-lookup"><span data-stu-id="c7e58-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="c7e58-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7e58-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c7e58-141">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e58-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="c7e58-142">Cláusula Distinct</span><span class="sxs-lookup"><span data-stu-id="c7e58-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="c7e58-143">Como: combinar e comparar coleções de cadeias de caracteres (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e58-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="c7e58-144">Como localizar a diferença de conjunto entre duas listas (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e58-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
