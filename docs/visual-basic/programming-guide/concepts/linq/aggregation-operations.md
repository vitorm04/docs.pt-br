---
title: Operações de agregação (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2f4234b9f56794b9bfe6c56029ccc9c00ae0642
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="f6328-102">Operações de agregação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6328-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="f6328-103">Uma operação de agregação computa um único valor de uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="f6328-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="f6328-104">Um exemplo de uma operação de agregação é o cálculo da temperatura média diária dos valores válidos de temperatura diária de um mês.</span><span class="sxs-lookup"><span data-stu-id="f6328-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="f6328-105">A ilustração a seguir mostra os resultados de duas operações de agregação diferentes em uma sequência de números.</span><span class="sxs-lookup"><span data-stu-id="f6328-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="f6328-106">A primeira operação soma os números.</span><span class="sxs-lookup"><span data-stu-id="f6328-106">The first operation sums the numbers.</span></span> <span data-ttu-id="f6328-107">A segunda operação retorna o valor máximo na sequência.</span><span class="sxs-lookup"><span data-stu-id="f6328-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="f6328-108">![Operações de agregação LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="f6328-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="f6328-109">Os métodos de operador de consulta padrão que realizam operações de agregação são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="f6328-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6328-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="f6328-110">Methods</span></span>  
  
|<span data-ttu-id="f6328-111">Nome do método</span><span class="sxs-lookup"><span data-stu-id="f6328-111">Method Name</span></span>|<span data-ttu-id="f6328-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6328-112">Description</span></span>|<span data-ttu-id="f6328-113">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6328-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f6328-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="f6328-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="f6328-115">Agregado</span><span class="sxs-lookup"><span data-stu-id="f6328-115">Aggregate</span></span>|<span data-ttu-id="f6328-116">Executa uma operação de agregação personalizada nos valores de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f6328-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="f6328-117">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="f6328-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f6328-118">Média</span><span class="sxs-lookup"><span data-stu-id="f6328-118">Average</span></span>|<span data-ttu-id="f6328-119">Calcula o valor médio de uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="f6328-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f6328-120">Contagem</span><span class="sxs-lookup"><span data-stu-id="f6328-120">Count</span></span>|<span data-ttu-id="f6328-121">Conta os elementos em uma coleção e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="f6328-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f6328-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="f6328-122">LongCount</span></span>|<span data-ttu-id="f6328-123">Conta os elementos em uma coleção grande e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="f6328-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f6328-124">Máx.</span><span class="sxs-lookup"><span data-stu-id="f6328-124">Max</span></span>|<span data-ttu-id="f6328-125">Determina o valor máximo em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f6328-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f6328-126">Mín.</span><span class="sxs-lookup"><span data-stu-id="f6328-126">Min</span></span>|<span data-ttu-id="f6328-127">Retorna o valor mínimo em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f6328-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f6328-128">Sum</span><span class="sxs-lookup"><span data-stu-id="f6328-128">Sum</span></span>|<span data-ttu-id="f6328-129">Calcula a soma dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f6328-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f6328-130">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="f6328-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="f6328-131">Média</span><span class="sxs-lookup"><span data-stu-id="f6328-131">Average</span></span>  
 <span data-ttu-id="f6328-132">O seguinte exemplo de código usa o `Aggregate Into Average` cláusula no Visual Basic para calcular a temperatura média em uma matriz de números que representam temperaturas.</span><span class="sxs-lookup"><span data-stu-id="f6328-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a><span data-ttu-id="f6328-133">Contagem</span><span class="sxs-lookup"><span data-stu-id="f6328-133">Count</span></span>  
 <span data-ttu-id="f6328-134">O seguinte exemplo de código usa o `Aggregate Into Count` cláusula no Visual Basic para contar o número de valores em uma matriz que são maiores que ou igual a 80.</span><span class="sxs-lookup"><span data-stu-id="f6328-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a><span data-ttu-id="f6328-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="f6328-135">LongCount</span></span>  
 <span data-ttu-id="f6328-136">O seguinte exemplo de código usa o `Aggregate Into LongCount` cláusula para contar o número de valores em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="f6328-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a><span data-ttu-id="f6328-137">Máx.</span><span class="sxs-lookup"><span data-stu-id="f6328-137">Max</span></span>  
 <span data-ttu-id="f6328-138">O seguinte exemplo de código usa o `Aggregate Into Max` cláusula para calcular a temperatura máxima em uma matriz de números que representam temperaturas.</span><span class="sxs-lookup"><span data-stu-id="f6328-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a><span data-ttu-id="f6328-139">Mín.</span><span class="sxs-lookup"><span data-stu-id="f6328-139">Min</span></span>  
 <span data-ttu-id="f6328-140">O seguinte exemplo de código usa o `Aggregate Into Min` cláusula para calcular a temperatura mínimo em uma matriz de números que representam temperaturas.</span><span class="sxs-lookup"><span data-stu-id="f6328-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a><span data-ttu-id="f6328-141">Sum</span><span class="sxs-lookup"><span data-stu-id="f6328-141">Sum</span></span>  
 <span data-ttu-id="f6328-142">O seguinte exemplo de código usa o `Aggregate Into Sum` cláusula para calcular a quantidade total de despesas de uma matriz de valores que representam as despesas.</span><span class="sxs-lookup"><span data-stu-id="f6328-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f6328-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6328-143">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="f6328-144">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6328-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="f6328-145">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="f6328-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="f6328-146">Como: computar valores de coluna em um arquivo de texto CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6328-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [<span data-ttu-id="f6328-147">Como contar, somar ou fazer média de dados</span><span class="sxs-lookup"><span data-stu-id="f6328-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [<span data-ttu-id="f6328-148">Como localizar o valor mínimo ou máximo em um resultado de consulta</span><span class="sxs-lookup"><span data-stu-id="f6328-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [<span data-ttu-id="f6328-149">Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6328-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [<span data-ttu-id="f6328-150">Como: consulta para o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6328-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
