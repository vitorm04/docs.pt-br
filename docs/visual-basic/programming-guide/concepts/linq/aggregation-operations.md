---
title: Operações de agregação
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 5c7f9344d379af2fed2a8f3d9f7c031c8ca00e8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345784"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="4445c-102">Operações de agregação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4445c-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="4445c-103">Uma operação de agregação computa um único valor de uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="4445c-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="4445c-104">Um exemplo de uma operação de agregação é o cálculo da temperatura média diária dos valores válidos de temperatura diária de um mês.</span><span class="sxs-lookup"><span data-stu-id="4445c-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="4445c-105">A ilustração a seguir mostra os resultados de duas operações de agregação diferentes em uma sequência de números.</span><span class="sxs-lookup"><span data-stu-id="4445c-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="4445c-106">A primeira operação soma os números.</span><span class="sxs-lookup"><span data-stu-id="4445c-106">The first operation sums the numbers.</span></span> <span data-ttu-id="4445c-107">A segunda operação retorna o valor máximo na sequência.</span><span class="sxs-lookup"><span data-stu-id="4445c-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![Ilustração que mostra operações de agregação LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="4445c-109">Os métodos de operador de consulta padrão que realizam operações de agregação são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="4445c-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4445c-110">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4445c-110">Methods</span></span>  
  
|<span data-ttu-id="4445c-111">Nome do método</span><span class="sxs-lookup"><span data-stu-id="4445c-111">Method Name</span></span>|<span data-ttu-id="4445c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4445c-112">Description</span></span>|<span data-ttu-id="4445c-113">Visual Basic sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="4445c-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="4445c-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="4445c-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="4445c-115">Agregado</span><span class="sxs-lookup"><span data-stu-id="4445c-115">Aggregate</span></span>|<span data-ttu-id="4445c-116">Executa uma operação de agregação personalizada nos valores de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="4445c-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="4445c-117">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4445c-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4445c-118">Média</span><span class="sxs-lookup"><span data-stu-id="4445c-118">Average</span></span>|<span data-ttu-id="4445c-119">Calcula o valor médio de uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="4445c-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4445c-120">{1&gt;{2&gt;Contagem&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4445c-120">Count</span></span>|<span data-ttu-id="4445c-121">Conta os elementos em uma coleção e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="4445c-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4445c-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="4445c-122">LongCount</span></span>|<span data-ttu-id="4445c-123">Conta os elementos em uma coleção grande e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="4445c-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4445c-124">Max</span><span class="sxs-lookup"><span data-stu-id="4445c-124">Max</span></span>|<span data-ttu-id="4445c-125">Determina o valor máximo em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="4445c-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4445c-126">Min</span><span class="sxs-lookup"><span data-stu-id="4445c-126">Min</span></span>|<span data-ttu-id="4445c-127">Retorna o valor mínimo em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="4445c-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4445c-128">Sum</span><span class="sxs-lookup"><span data-stu-id="4445c-128">Sum</span></span>|<span data-ttu-id="4445c-129">Calcula a soma dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="4445c-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="4445c-130">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="4445c-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="4445c-131">Média</span><span class="sxs-lookup"><span data-stu-id="4445c-131">Average</span></span>  
 <span data-ttu-id="4445c-132">O exemplo de código a seguir usa a cláusula `Aggregate Into Average` em Visual Basic para calcular a temperatura média em uma matriz de números que representam temperaturas.</span><span class="sxs-lookup"><span data-stu-id="4445c-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="4445c-133">{1&gt;{2&gt;Contagem&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4445c-133">Count</span></span>  
 <span data-ttu-id="4445c-134">O exemplo de código a seguir usa a cláusula `Aggregate Into Count` em Visual Basic para contar o número de valores em uma matriz que é maior ou igual a 80.</span><span class="sxs-lookup"><span data-stu-id="4445c-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="4445c-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="4445c-135">LongCount</span></span>  
 <span data-ttu-id="4445c-136">O exemplo de código a seguir usa a cláusula `Aggregate Into LongCount` para contar o número de valores em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="4445c-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="4445c-137">Max</span><span class="sxs-lookup"><span data-stu-id="4445c-137">Max</span></span>  
 <span data-ttu-id="4445c-138">O exemplo de código a seguir usa a cláusula `Aggregate Into Max` para calcular a temperatura máxima em uma matriz de números que representam temperaturas.</span><span class="sxs-lookup"><span data-stu-id="4445c-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="4445c-139">Min</span><span class="sxs-lookup"><span data-stu-id="4445c-139">Min</span></span>  
 <span data-ttu-id="4445c-140">O exemplo de código a seguir usa a cláusula `Aggregate Into Min` para calcular a temperatura mínima em uma matriz de números que representam temperaturas.</span><span class="sxs-lookup"><span data-stu-id="4445c-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="4445c-141">Sum</span><span class="sxs-lookup"><span data-stu-id="4445c-141">Sum</span></span>  
 <span data-ttu-id="4445c-142">O exemplo de código a seguir usa a cláusula `Aggregate Into Sum` para calcular o valor total das despesas de uma matriz de valores que representam as despesas.</span><span class="sxs-lookup"><span data-stu-id="4445c-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4445c-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4445c-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="4445c-144">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4445c-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4445c-145">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="4445c-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="4445c-146">Como: calcular valores de coluna em um arquivo de texto CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4445c-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="4445c-147">Como contar, somar ou fazer média de dados</span><span class="sxs-lookup"><span data-stu-id="4445c-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="4445c-148">Como localizar o valor mínimo ou máximo em um resultado de consulta</span><span class="sxs-lookup"><span data-stu-id="4445c-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="4445c-149">Como consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4445c-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="4445c-150">Como consultar o número total de bytes em um conjunto de pastas (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4445c-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
