---
title: Conversão padrão de operador de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 280557a5098c513111557f52d835b20d9a2eeb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876871"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="2e4fa-102">Conversão padrão de operador de consulta</span><span class="sxs-lookup"><span data-stu-id="2e4fa-102">Standard Query Operator Translation</span></span>

<span data-ttu-id="2e4fa-103">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte operadores de consulta padrão em comandos SQL.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="2e4fa-104">O processador de consultas do banco de dados determina a semântica de execução de conversão SQL.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="2e4fa-105">Operadores de consulta padrão são definidos em relação a *sequências*.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="2e4fa-106">É uma sequência *ordenados* e depende da identidade de referência para cada elemento da sequência.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="2e4fa-107">Para obter mais informações, consulte [visão geral de operadores de consulta padrão (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ou [visão geral de operadores padrão consulta (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-107">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="2e4fa-108">SQL trata principalmente *desordenados conjuntos de valores*.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="2e4fa-109">A ordenação normalmente é indicada explicitamente, uma operação de pós-processamento que é aplicada ao resultado final de uma consulta em vez de aos resultados intermediários.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="2e4fa-110">A identidade é definida por valores.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-110">Identity is defined by values.</span></span> <span data-ttu-id="2e4fa-111">Por esse motivo, as consultas SQL são supostas a manipular multisets (*recipientes*) em vez de *define*.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="2e4fa-112">Os parágrafos a seguir descrevem as diferenças entre os operadores de consulta padrão e sua conversão SQL do provedor SQL Server para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="2e4fa-113">Suporte de operador</span><span class="sxs-lookup"><span data-stu-id="2e4fa-113">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="2e4fa-114">Concat</span><span class="sxs-lookup"><span data-stu-id="2e4fa-114">Concat</span></span>

<span data-ttu-id="2e4fa-115">O método <xref:System.Linq.Enumerable.Concat%2A> é definido para multisets ordenados onde a ordem do receptor e a ordem do argumento são as mesmas.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="2e4fa-116">O <xref:System.Linq.Enumerable.Concat%2A> funciona como `UNION ALL` sobre os multisets seguido pela ordem comum.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="2e4fa-117">A etapa final é ordenar no SQL antes que os resultados sejam produzidos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="2e4fa-118">O <xref:System.Linq.Enumerable.Concat%2A> não preserva a ordem de seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="2e4fa-119">Para garantir a ordem apropriada, você deve ordenar explicitamente os resultados de <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="2e4fa-120">Intersect, Except, Union</span><span class="sxs-lookup"><span data-stu-id="2e4fa-120">Intersect, Except, Union</span></span>

<span data-ttu-id="2e4fa-121">Os métodos <xref:System.Linq.Enumerable.Intersect%2A> e <xref:System.Linq.Enumerable.Except%2A> são bem-definidos somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="2e4fa-122">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-122">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="2e4fa-123">O método <xref:System.Linq.Enumerable.Union%2A> é definido para multisets como a concatenação não ordenada dos multisets (efetivamente o resultado da cláusula UNION ALL no SQL).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="2e4fa-124">Take, Skip</span><span class="sxs-lookup"><span data-stu-id="2e4fa-124">Take, Skip</span></span>

<span data-ttu-id="2e4fa-125"><xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> métodos são bem-definidos somente em *conjuntos ordenados*.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="2e4fa-126">A semântica de conjuntos ou de multisets não ordenados é indefinida.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-126">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="2e4fa-127"><xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> possuem certas limitações quando são usados em consultas no SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="2e4fa-128">Para obter mais informações, consulte a entrada "Exceções Skip e Take no SQL Server 2000" em [solução de problemas](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>

<span data-ttu-id="2e4fa-129">Devido às limitações de ordenamento no SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta mover ordenação do argumento desses métodos para o resultado do método.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="2e4fa-130">Por exemplo, considere a seguinte consulta [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="2e4fa-131">O SQL gerado para esse código move a ordenação para o final, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="2e4fa-132">Torna-se óbvio que qualquer ordenação especificada precisa ser consistente quando <xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> são encadeados juntos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="2e4fa-133">Caso contrário, os resultados serão indefinidos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-133">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="2e4fa-134"><xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> são definidos para argumentos inteiros não negativos, argumentos integrais constantes baseados na especificação de operador de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="2e4fa-135">Operadores sem a conversão</span><span class="sxs-lookup"><span data-stu-id="2e4fa-135">Operators with No Translation</span></span>

<span data-ttu-id="2e4fa-136">Os seguintes métodos não são convertidos pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2e4fa-137">O motivo mais comum é a diferença entre multisets e sequências não ordenados.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-137">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="2e4fa-138">Operadores</span><span class="sxs-lookup"><span data-stu-id="2e4fa-138">Operators</span></span>|<span data-ttu-id="2e4fa-139">Racional</span><span class="sxs-lookup"><span data-stu-id="2e4fa-139">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="2e4fa-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="2e4fa-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="2e4fa-141">Consultas SQL operam em multisets, não em sequências.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="2e4fa-142">`ORDER BY` deve ser a última cláusula aplicada aos resultados.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="2e4fa-143">Por esse motivo, não há nenhuma conversão de finalidade geral para esses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="2e4fa-144">A conversão desse método é possível para um conjunto ordenado, mas, no momento, não é convertido pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="2e4fa-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="2e4fa-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="2e4fa-146">A conversão desses métodos é possível para um conjunto ordenado, mas, no momento, não são convertidos pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="2e4fa-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="2e4fa-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="2e4fa-148">As consultas SQL operam em multisets, não em sequências indexáveis.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="2e4fa-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (sobrecarga com arg padrão)</span><span class="sxs-lookup"><span data-stu-id="2e4fa-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="2e4fa-150">Em geral, um valor padrão não pode ser especificado para um tuple arbitrário.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="2e4fa-151">Valores nulos para tuples são possíveis em alguns casos com junções externas.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-151">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="2e4fa-152">Conversão de expressão</span><span class="sxs-lookup"><span data-stu-id="2e4fa-152">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="2e4fa-153">Semântica de nulo</span><span class="sxs-lookup"><span data-stu-id="2e4fa-153">Null semantics</span></span>

<span data-ttu-id="2e4fa-154">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não impõe semântica de comparação de nulo no SQL.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-154">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="2e4fa-155">Os operadores de comparação são convertidos sintaticamente para seus equivalentes SQL.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="2e4fa-156">Por esse motivo, a semântica reflete a semântica do SQL que é definida pelas configurações do servidor ou conexão.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="2e4fa-157">Por exemplo, dois valores nulos são considerados desiguais com configurações padrão do SQL Server, mas você pode alterar as configurações para alterar a semântica.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> <span data-ttu-id="2e4fa-158">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não considera as configurações do servidor quando converte consultas.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-158">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="2e4fa-159">Uma comparação com o nulo literal é convertida na versão apropriada do SQL (`is null` ou `is not null`).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="2e4fa-160">O valor de `null` na ordenação é definido pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-160">The value of `null` in collation is defined by SQL Server.</span></span> <span data-ttu-id="2e4fa-161">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não altera a ordenação.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-161">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="2e4fa-162">Agregações</span><span class="sxs-lookup"><span data-stu-id="2e4fa-162">Aggregates</span></span>

<span data-ttu-id="2e4fa-163">O método de agregação do operador de consulta padrão <xref:System.Linq.Enumerable.Sum%2A> avalia uma sequência vazia ou uma sequência que contém somente nulos como zero.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="2e4fa-164">Na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a semântica do SQL é deixada inalterado, e <xref:System.Linq.Enumerable.Sum%2A> é avaliada como `null` em vez de zero para uma sequência vazia ou uma sequência que contém somente nulos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="2e4fa-165">As limitações do SQL em resultados intermediários se aplicam às agregações no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2e4fa-166">O <xref:System.Linq.Enumerable.Sum%2A> de inteiro de 32 bits quantidades não é computada usando resultados de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="2e4fa-167">Estouro pode ocorrer para um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tradução de <xref:System.Linq.Enumerable.Sum%2A>, mesmo se a implementação do operador de consulta padrão não causa um estouro para a sequência de memória correspondente.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="2e4fa-168">Da mesma forma, a conversão de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de valores inteiros do <xref:System.Linq.Enumerable.Average%2A> é computada como um `integer`, não como um `double`.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="2e4fa-169">Argumentos de entidade</span><span class="sxs-lookup"><span data-stu-id="2e4fa-169">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2e4fa-170">permite que os tipos de entidade a ser usado na <xref:System.Linq.Enumerable.GroupBy%2A> e <xref:System.Linq.Enumerable.OrderBy%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-170">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="2e4fa-171">Na conversão desses operadores, o uso de um argumento de um tipo é considerado ser o equivalente a especificar todos os membros desse tipo.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="2e4fa-172">Por exemplo, o código a seguir é equivalente:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-172">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="2e4fa-173">Argumentos equitativos/comparáveis</span><span class="sxs-lookup"><span data-stu-id="2e4fa-173">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="2e4fa-174">A igualdade dos argumentos é necessária na implementação dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-174">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2e4fa-175">dá suporte à igualdade e à comparação *simples* argumentos, mas não para argumentos que são ou contêm sequências.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-175">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="2e4fa-176">Um argumento simples é um tipo que pode ser mapeado para uma linha SQL.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="2e4fa-177">Uma projeção de um ou mais tipos de entidade, que podem ser determinados estaticamente por não conterem uma sequência, é considerada um argumento simples.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="2e4fa-178">Os seguintes são exemplos de argumentos simples:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-178">Following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="2e4fa-179">Os seguintes são exemplos de argumentos que não são simples (hierárquicos).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-179">The following are examples of non-flat (hierarchical) arguments.</span></span>

[!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="2e4fa-180">Conversão de função do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e4fa-180">Visual Basic Function Translation</span></span>

<span data-ttu-id="2e4fa-181">As seguintes funções auxiliares que são usadas pelo compilador Visual Basic são convertidas em operadores e funções SQL correspondentes:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="2e4fa-182">Métodos de conversão:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-182">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="2e4fa-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="2e4fa-183">ToBoolean</span></span>|<span data-ttu-id="2e4fa-184">ToSByte</span><span class="sxs-lookup"><span data-stu-id="2e4fa-184">ToSByte</span></span>|<span data-ttu-id="2e4fa-185">ToByte</span><span class="sxs-lookup"><span data-stu-id="2e4fa-185">ToByte</span></span>|<span data-ttu-id="2e4fa-186">ToChar</span><span class="sxs-lookup"><span data-stu-id="2e4fa-186">ToChar</span></span>|
|<span data-ttu-id="2e4fa-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="2e4fa-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="2e4fa-188">ToDate</span><span class="sxs-lookup"><span data-stu-id="2e4fa-188">ToDate</span></span>|<span data-ttu-id="2e4fa-189">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="2e4fa-189">ToDecimal</span></span>|<span data-ttu-id="2e4fa-190">ToDouble</span><span class="sxs-lookup"><span data-stu-id="2e4fa-190">ToDouble</span></span>|
|<span data-ttu-id="2e4fa-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="2e4fa-191">ToInteger</span></span>|<span data-ttu-id="2e4fa-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="2e4fa-192">ToUInteger</span></span>|<span data-ttu-id="2e4fa-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="2e4fa-193">ToLong</span></span>|<span data-ttu-id="2e4fa-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="2e4fa-194">ToULong</span></span>|
|<span data-ttu-id="2e4fa-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="2e4fa-195">ToShort</span></span>|<span data-ttu-id="2e4fa-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="2e4fa-196">ToUShort</span></span>|<span data-ttu-id="2e4fa-197">ToSingle</span><span class="sxs-lookup"><span data-stu-id="2e4fa-197">ToSingle</span></span>|<span data-ttu-id="2e4fa-198">ToString</span><span class="sxs-lookup"><span data-stu-id="2e4fa-198">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="2e4fa-199">Suporte à herança</span><span class="sxs-lookup"><span data-stu-id="2e4fa-199">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="2e4fa-200">Restrições de mapeamento de herança</span><span class="sxs-lookup"><span data-stu-id="2e4fa-200">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="2e4fa-201">Para obter mais informações, confira [Como: Mapear hierarquias de herança](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-201">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="2e4fa-202">Herança em consultas</span><span class="sxs-lookup"><span data-stu-id="2e4fa-202">Inheritance in Queries</span></span>

<span data-ttu-id="2e4fa-203">As conversões do C# são suportadas apenas na projeção.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="2e4fa-204">Conversões que são usadas em outro lugar não são convertidas e são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="2e4fa-205">Com exceção dos nomes de funções SQL, o SQL realmente executa apenas o equivalente do <xref:System.Convert> do CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="2e4fa-206">Isto é, o SQL pode alterar o valor de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="2e4fa-207">Não há nenhum equivalente de conversão do CLR porque não há nenhum conceito de reinterpretação dos mesmos bits como os de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="2e4fa-208">É por isso que uma conversão C# funciona apenas localmente.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="2e4fa-209">Ela não funciona remotamente.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-209">It is not remoted.</span></span>

<span data-ttu-id="2e4fa-210">Os operadores `is` e `as` e o método `GetType` não são restritos ao operador `Select`.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="2e4fa-211">Podem ser usados em outros operadores de consulta também.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-211">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="2e4fa-212">SQL Server 2008 Support</span><span class="sxs-lookup"><span data-stu-id="2e4fa-212">SQL Server 2008 Support</span></span>

<span data-ttu-id="2e4fa-213">A partir do .NET Framework 3.5 SP1, o LINQ to SQL dá suporte ao mapeamento para novos tipos de data e hora introduzidos com o SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="2e4fa-214">Mas, há algumas limitações aos operadores de consulta do LINQ to SQL que você pode usar ao operar com valores mapeados para esses novos tipos.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="2e4fa-215">Operadores de consulta não suportados</span><span class="sxs-lookup"><span data-stu-id="2e4fa-215">Unsupported Query Operators</span></span>

<span data-ttu-id="2e4fa-216">Os seguintes operadores de consulta não são suportados em valores mapeados para novos tipos de data e hora do SQL Server: `DATETIME2`, `DATE`, `TIME` e `DATETIMEOFFSET`.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="2e4fa-217">Para obter mais informações sobre o mapeamento para esses tipos de data e hora do SQL Server, consulte [mapeamento de tipo CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="2e4fa-218">SQL Server 2005 Support</span><span class="sxs-lookup"><span data-stu-id="2e4fa-218">SQL Server 2005 Support</span></span>

<span data-ttu-id="2e4fa-219">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não dá suporte aos seguintes recursos do SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-219">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="2e4fa-220">Procedimentos armazenados escritos para SQL CLR.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-220">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="2e4fa-221">Tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-221">User-defined type.</span></span>

- <span data-ttu-id="2e4fa-222">Recursos de consulta XML.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-222">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="2e4fa-223">Suporte do SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="2e4fa-223">SQL Server 2000 Support</span></span>

<span data-ttu-id="2e4fa-224">As seguintes limitações do [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] (em comparação com o [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) afetam o suporte ao [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-224">The following [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] limitations (compared to [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="2e4fa-225">Operadores Cross Apply e Outer Apply</span><span class="sxs-lookup"><span data-stu-id="2e4fa-225">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="2e4fa-226">Esses operadores não estão disponíveis no [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-226">These operators are not available in [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> <span data-ttu-id="2e4fa-227">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta uma série de reescritas para substituí-los com junções apropriadas.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-227">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="2e4fa-228">O `Cross Apply` e o `Outer Apply` são gerados para navegações de relacionamento.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="2e4fa-229">O conjunto de consultas para as quais essas reescritas são possíveis não é bem definido.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="2e4fa-230">Por esse motivo, o conjunto mínimo de consultas que é suportado para o [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] é o conjunto que não envolve a navegação de relacionamento.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-230">For this reason, the minimal set of queries that is supported for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="2e4fa-231">text/ntext</span><span class="sxs-lookup"><span data-stu-id="2e4fa-231">text / ntext</span></span>

<span data-ttu-id="2e4fa-232">Tipos de dados `text`  /  `ntext` não pode ser usado em determinadas operações de consulta em relação a `varchar(max)`  /  `nvarchar(max)`, que são suportados por [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span></span>

<span data-ttu-id="2e4fa-233">Nenhuma resolução está disponível para essa limitação.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="2e4fa-234">Especificamente, você não pode usar `Distinct()` em resultados que contêm membros que são mapeados para colunas `text` ou `ntext`.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="2e4fa-235">Comportamento disparado por consultas aninhadas</span><span class="sxs-lookup"><span data-stu-id="2e4fa-235">Behavior Triggered by Nested Queries</span></span>

[!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] <span data-ttu-id="2e4fa-236">(por meio do SP4) associador tem algumas Idiossincrasias que são disparadas por consultas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-236">(through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="2e4fa-237">O conjunto de consultas SQL que dispara essas Idiossincrasias não é bem definido.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="2e4fa-238">Por esse motivo, você não pode definir o conjunto de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consultas que podem causar exceções do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="2e4fa-239">Operadores Skip e Take</span><span class="sxs-lookup"><span data-stu-id="2e4fa-239">Skip and Take Operators</span></span>

<span data-ttu-id="2e4fa-240"><xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> possuem certas limitações quando são usados em consultas no [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4fa-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> <span data-ttu-id="2e4fa-241">Para obter mais informações, consulte a entrada "Exceções Skip e Take no SQL Server 2000" em [solução de problemas](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="2e4fa-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="2e4fa-242">Materialização de objetos</span><span class="sxs-lookup"><span data-stu-id="2e4fa-242">Object Materialization</span></span>

<span data-ttu-id="2e4fa-243">A materialização cria objetos CLR das linhas que são retornadas por uma ou mais consultas SQL.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="2e4fa-244">São as seguintes chamadas *executado localmente* como parte da materialização:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-244">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="2e4fa-245">Construtores</span><span class="sxs-lookup"><span data-stu-id="2e4fa-245">Constructors</span></span>

  - <span data-ttu-id="2e4fa-246">Métodos `ToString` em projeções</span><span class="sxs-lookup"><span data-stu-id="2e4fa-246">`ToString` methods in projections</span></span>

  - <span data-ttu-id="2e4fa-247">Conversões de tipos em projeções</span><span class="sxs-lookup"><span data-stu-id="2e4fa-247">Type casts in projections</span></span>

- <span data-ttu-id="2e4fa-248">Métodos que seguem a <xref:System.Linq.Enumerable.AsEnumerable%2A> método estão *executado localmente*.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="2e4fa-249">Esse método não provoca uma execução imediata.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-249">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="2e4fa-250">Você pode usar `struct` como o tipo de retorno de um resultado de consulta ou como um membro do tipo de resultado.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="2e4fa-251">As entidades precisam ser classes.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-251">Entities are required to be classes.</span></span> <span data-ttu-id="2e4fa-252">Tipos anônimos são materializados como instâncias de classe, mas structs nomeados (não entidades) podem ser usados na projeção.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="2e4fa-253">Um membro do tipo do retorno de um resultado de consulta pode ser do tipo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="2e4fa-254">É materializado como uma coleção local.</span><span class="sxs-lookup"><span data-stu-id="2e4fa-254">It is materialized as a local collection.</span></span>

- <span data-ttu-id="2e4fa-255">Os seguintes métodos provocam a *materialização imediata* da sequência em que os métodos são aplicados a:</span><span class="sxs-lookup"><span data-stu-id="2e4fa-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="2e4fa-256">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e4fa-256">See also</span></span>

- [<span data-ttu-id="2e4fa-257">Referência</span><span class="sxs-lookup"><span data-stu-id="2e4fa-257">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="2e4fa-258">Retornar ou ignorar elementos em uma sequência</span><span class="sxs-lookup"><span data-stu-id="2e4fa-258">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="2e4fa-259">Concatenar duas sequências</span><span class="sxs-lookup"><span data-stu-id="2e4fa-259">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)
- [<span data-ttu-id="2e4fa-260">Retornar a diferença de conjunto entre duas sequências</span><span class="sxs-lookup"><span data-stu-id="2e4fa-260">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="2e4fa-261">Retornar a interseção de conjunto de duas sequências</span><span class="sxs-lookup"><span data-stu-id="2e4fa-261">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="2e4fa-262">Retornar a união de conjunto de duas sequências</span><span class="sxs-lookup"><span data-stu-id="2e4fa-262">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
