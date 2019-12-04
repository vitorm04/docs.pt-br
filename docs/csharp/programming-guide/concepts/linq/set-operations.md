---
title: Operações de conjunto (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 22079b1d41533803f694af210f98bc9fb8a5b322
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711878"
---
# <a name="set-operations-c"></a><span data-ttu-id="f5865-102">Operações de conjunto (C#)</span><span class="sxs-lookup"><span data-stu-id="f5865-102">Set Operations (C#)</span></span>
<span data-ttu-id="f5865-103">As operações de conjunto na LINQ referem-se a operações de consulta que geram um conjunto de resultados baseado na presença ou ausência de elementos equivalentes dentro da mesma ou de coleções (ou conjuntos) separadas.</span><span class="sxs-lookup"><span data-stu-id="f5865-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="f5865-104">Os métodos de operador de consulta padrão que executam operações de conjunto estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5865-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5865-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f5865-105">Methods</span></span>  
  
|<span data-ttu-id="f5865-106">Nome do método</span><span class="sxs-lookup"><span data-stu-id="f5865-106">Method Name</span></span>|<span data-ttu-id="f5865-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5865-107">Description</span></span>|<span data-ttu-id="f5865-108">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="f5865-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="f5865-109">Mais Informações</span><span class="sxs-lookup"><span data-stu-id="f5865-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f5865-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="f5865-110">Distinct</span></span>|<span data-ttu-id="f5865-111">Remove os valores duplicados de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f5865-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="f5865-112">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f5865-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5865-113">Exceto</span><span class="sxs-lookup"><span data-stu-id="f5865-113">Except</span></span>|<span data-ttu-id="f5865-114">Retorna a diferença de conjunto, que significa os elementos de uma coleção que não aparecem em uma segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="f5865-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="f5865-115">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f5865-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5865-116">Interseção</span><span class="sxs-lookup"><span data-stu-id="f5865-116">Intersect</span></span>|<span data-ttu-id="f5865-117">Retorna a interseção de conjunto, o que significa os elementos que aparecem em cada uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="f5865-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="f5865-118">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f5865-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5865-119">Union</span><span class="sxs-lookup"><span data-stu-id="f5865-119">Union</span></span>|<span data-ttu-id="f5865-120">Retorna a união de conjunto, o que significa os elementos únicos que aparecem em qualquer uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="f5865-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="f5865-121">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f5865-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="f5865-122">Comparação de operações de conjuntos</span><span class="sxs-lookup"><span data-stu-id="f5865-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="f5865-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="f5865-123">Distinct</span></span>  
 <span data-ttu-id="f5865-124">O exemplo a seguir descreve o comportamento do método <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f5865-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="f5865-125">A sequência retornada contém os elementos exclusivos da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="f5865-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
 
 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="f5865-127">Exceto</span><span class="sxs-lookup"><span data-stu-id="f5865-127">Except</span></span>  
 <span data-ttu-id="f5865-128">O exemplo a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5865-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5865-129">A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="f5865-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="f5865-130">![Gráfico mostrando a ação de Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Mostra o comportamento de Except.")</span><span class="sxs-lookup"><span data-stu-id="f5865-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="f5865-131">Interseção</span><span class="sxs-lookup"><span data-stu-id="f5865-131">Intersect</span></span>  
 <span data-ttu-id="f5865-132">O exemplo a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5865-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5865-133">A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.</span><span class="sxs-lookup"><span data-stu-id="f5865-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Gráfico mostrando a interseção de duas sequências.](./media/set-operations/intersection-two-sequences.png)  
 
[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="f5865-135">Union</span><span class="sxs-lookup"><span data-stu-id="f5865-135">Union</span></span>  
 <span data-ttu-id="f5865-136">O exemplo a seguir descreve uma operação Union em duas sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f5865-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="f5865-137">A sequência retornada contém os elementos exclusivos das duas sequências de entrada.</span><span class="sxs-lookup"><span data-stu-id="f5865-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Gráfico mostrando a união de duas sequências.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]
 
## <a name="see-also"></a><span data-ttu-id="f5865-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5865-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f5865-140">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="f5865-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="f5865-141">Como combinar e comparar coleções de cadeias de caracteres (C#LINQ) ()</span><span class="sxs-lookup"><span data-stu-id="f5865-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="f5865-142">Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f5865-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
