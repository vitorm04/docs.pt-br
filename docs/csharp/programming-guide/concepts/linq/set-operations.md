---
title: Operações de conjunto (C#)
description: Saiba mais sobre as operações set e os métodos do operador de consulta padrão que executam operações Set no LINQ em C#.
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: ab2608b267113ad5d47a33e64cd9a5e21496f668
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302367"
---
# <a name="set-operations-c"></a><span data-ttu-id="ad25e-103">Operações de conjunto (C#)</span><span class="sxs-lookup"><span data-stu-id="ad25e-103">Set Operations (C#)</span></span>
<span data-ttu-id="ad25e-104">As operações de conjunto na LINQ referem-se a operações de consulta que geram um conjunto de resultados baseado na presença ou ausência de elementos equivalentes dentro da mesma ou de coleções (ou conjuntos) separadas.</span><span class="sxs-lookup"><span data-stu-id="ad25e-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="ad25e-105">Os métodos de operador de consulta padrão que executam operações de conjunto estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad25e-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad25e-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="ad25e-106">Methods</span></span>  
  
|<span data-ttu-id="ad25e-107">Nome do método</span><span class="sxs-lookup"><span data-stu-id="ad25e-107">Method Name</span></span>|<span data-ttu-id="ad25e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad25e-108">Description</span></span>|<span data-ttu-id="ad25e-109">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="ad25e-109">C# Query Expression Syntax</span></span>|<span data-ttu-id="ad25e-110">Mais informações</span><span class="sxs-lookup"><span data-stu-id="ad25e-110">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ad25e-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="ad25e-111">Distinct</span></span>|<span data-ttu-id="ad25e-112">Remove os valores duplicados de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="ad25e-112">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="ad25e-113">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="ad25e-113">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ad25e-114">Except</span><span class="sxs-lookup"><span data-stu-id="ad25e-114">Except</span></span>|<span data-ttu-id="ad25e-115">Retorna a diferença de conjunto, que significa os elementos de uma coleção que não aparecem em uma segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="ad25e-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="ad25e-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="ad25e-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ad25e-117">Intersect</span><span class="sxs-lookup"><span data-stu-id="ad25e-117">Intersect</span></span>|<span data-ttu-id="ad25e-118">Retorna a interseção de conjunto, o que significa os elementos que aparecem em cada uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="ad25e-118">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="ad25e-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="ad25e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ad25e-120">Union</span><span class="sxs-lookup"><span data-stu-id="ad25e-120">Union</span></span>|<span data-ttu-id="ad25e-121">Retorna a união de conjunto, o que significa os elementos únicos que aparecem em qualquer uma das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="ad25e-121">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="ad25e-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="ad25e-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="ad25e-123">Comparação de operações de conjuntos</span><span class="sxs-lookup"><span data-stu-id="ad25e-123">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="ad25e-124">Distinct</span><span class="sxs-lookup"><span data-stu-id="ad25e-124">Distinct</span></span>  
 <span data-ttu-id="ad25e-125">O exemplo a seguir descreve o comportamento do <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> método em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ad25e-125">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="ad25e-126">A sequência retornada contém os elementos exclusivos da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad25e-126">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="ad25e-128">Except</span><span class="sxs-lookup"><span data-stu-id="ad25e-128">Except</span></span>  
 <span data-ttu-id="ad25e-129">O exemplo a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ad25e-129">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad25e-130">A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad25e-130">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="ad25e-131">![Gráfico mostrando a ação de, exceto&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Mostra o comportamento de Except.")</span><span class="sxs-lookup"><span data-stu-id="ad25e-131">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="ad25e-132">Intersect</span><span class="sxs-lookup"><span data-stu-id="ad25e-132">Intersect</span></span>  
 <span data-ttu-id="ad25e-133">O exemplo a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ad25e-133">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad25e-134">A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad25e-134">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Gráfico mostrando a interseção de duas sequências.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="ad25e-136">Union</span><span class="sxs-lookup"><span data-stu-id="ad25e-136">Union</span></span>  
 <span data-ttu-id="ad25e-137">O exemplo a seguir descreve uma operação Union em duas sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ad25e-137">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="ad25e-138">A sequência retornada contém os elementos exclusivos das duas sequências de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad25e-138">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Gráfico mostrando a união de duas sequências.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="ad25e-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="ad25e-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ad25e-141">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="ad25e-141">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ad25e-142">Como combinar e comparar coleções de cadeias de caracteres (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ad25e-142">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="ad25e-143">Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ad25e-143">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
