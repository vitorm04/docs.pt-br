---
title: "Operações de agregação (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6c453bdccdb3af026fe4f4fb79c6e33e44e7a8f0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="aggregation-operations-c"></a><span data-ttu-id="77061-102">Operações de agregação (C#)</span><span class="sxs-lookup"><span data-stu-id="77061-102">Aggregation Operations (C#)</span></span>
<span data-ttu-id="77061-103">Uma operação de agregação computa um único valor de uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="77061-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="77061-104">Um exemplo de uma operação de agregação é o cálculo da temperatura média diária dos valores válidos de temperatura diária de um mês.</span><span class="sxs-lookup"><span data-stu-id="77061-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="77061-105">A ilustração a seguir mostra os resultados de duas operações de agregação diferentes em uma sequência de números.</span><span class="sxs-lookup"><span data-stu-id="77061-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="77061-106">A primeira operação soma os números.</span><span class="sxs-lookup"><span data-stu-id="77061-106">The first operation sums the numbers.</span></span> <span data-ttu-id="77061-107">A segunda operação retorna o valor máximo na sequência.</span><span class="sxs-lookup"><span data-stu-id="77061-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="77061-108">![Operações de agregação LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="77061-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="77061-109">Os métodos de operador de consulta padrão que realizam operações de agregação são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="77061-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77061-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="77061-110">Methods</span></span>  
  
|<span data-ttu-id="77061-111">Nome do método</span><span class="sxs-lookup"><span data-stu-id="77061-111">Method Name</span></span>|<span data-ttu-id="77061-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="77061-112">Description</span></span>|<span data-ttu-id="77061-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="77061-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="77061-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="77061-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="77061-115">Agregado</span><span class="sxs-lookup"><span data-stu-id="77061-115">Aggregate</span></span>|<span data-ttu-id="77061-116">Executa uma operação de agregação personalizada nos valores de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="77061-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="77061-117">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="77061-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=fullName>|  
|<span data-ttu-id="77061-118">Média</span><span class="sxs-lookup"><span data-stu-id="77061-118">Average</span></span>|<span data-ttu-id="77061-119">Calcula o valor médio de uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="77061-119">Calculates the average value of a collection of values.</span></span>|<span data-ttu-id="77061-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="77061-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Average%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=fullName>|  
|<span data-ttu-id="77061-121">Contagem</span><span class="sxs-lookup"><span data-stu-id="77061-121">Count</span></span>|<span data-ttu-id="77061-122">Conta os elementos em uma coleção e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="77061-122">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="77061-123">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="77061-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=fullName>|  
|<span data-ttu-id="77061-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="77061-124">LongCount</span></span>|<span data-ttu-id="77061-125">Conta os elementos em uma coleção grande e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="77061-125">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="77061-126">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="77061-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=fullName>|  
|<span data-ttu-id="77061-127">Máx.</span><span class="sxs-lookup"><span data-stu-id="77061-127">Max</span></span>|<span data-ttu-id="77061-128">Determina o valor máximo em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="77061-128">Determines the maximum value in a collection.</span></span>|<span data-ttu-id="77061-129">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="77061-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Max%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>|  
|<span data-ttu-id="77061-130">Mín.</span><span class="sxs-lookup"><span data-stu-id="77061-130">Min</span></span>|<span data-ttu-id="77061-131">Retorna o valor mínimo em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="77061-131">Determines the minimum value in a collection.</span></span>|<span data-ttu-id="77061-132">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="77061-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Min%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>|  
|<span data-ttu-id="77061-133">Sum</span><span class="sxs-lookup"><span data-stu-id="77061-133">Sum</span></span>|<span data-ttu-id="77061-134">Calcula a soma dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="77061-134">Calculates the sum of the values in a collection.</span></span>|<span data-ttu-id="77061-135">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="77061-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="77061-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77061-136">See Also</span></span>  
 <span data-ttu-id="77061-137"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="77061-137"><xref:System.Linq></span></span>   
 <span data-ttu-id="77061-138">[Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="77061-138">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="77061-139">[Como computar valores de coluna em um arquivo de texto CSV (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md) </span><span class="sxs-lookup"><span data-stu-id="77061-139">[How to: Compute Column Values in a CSV Text File (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md) </span></span>  
 <span data-ttu-id="77061-140">[Como consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md) </span><span class="sxs-lookup"><span data-stu-id="77061-140">[How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md) </span></span>  
 [<span data-ttu-id="77061-141">Como consultar o número total de bytes em um conjunto de pastas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="77061-141">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)

