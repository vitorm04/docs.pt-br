---
title: SELECIONAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: de6c497e7d781d705c68092e4a13ee07b727b2b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149903"
---
# <a name="select-entity-sql"></a><span data-ttu-id="85e16-102">SELECIONAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="85e16-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="85e16-103">Especifica os elementos retornados por uma consulta.</span><span class="sxs-lookup"><span data-stu-id="85e16-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85e16-104">Syntax</span></span>  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="85e16-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="85e16-105">Arguments</span></span>  
 <span data-ttu-id="85e16-106">ALL</span><span class="sxs-lookup"><span data-stu-id="85e16-106">ALL</span></span>  
 <span data-ttu-id="85e16-107">Especifica que as duplicatas podem aparecer no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="85e16-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="85e16-108">ALL é o padrão.</span><span class="sxs-lookup"><span data-stu-id="85e16-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="85e16-109">DISTINTO</span><span class="sxs-lookup"><span data-stu-id="85e16-109">DISTINCT</span></span>  
 <span data-ttu-id="85e16-110">Especifica que apenas resultados exclusivos podem aparecer no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="85e16-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="85e16-111">VALUE</span><span class="sxs-lookup"><span data-stu-id="85e16-111">VALUE</span></span>  
 <span data-ttu-id="85e16-112">Permite que somente um item seja especificado, e não adiciona um wrapper de linha.</span><span class="sxs-lookup"><span data-stu-id="85e16-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="85e16-113">Qualquer expressão válida que indique o número de primeiros `top(expr)`resultados a retornar da consulta, do formulário .</span><span class="sxs-lookup"><span data-stu-id="85e16-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="85e16-114">O parâmetro LIMITE do operador [ORDER BY](order-by-entity-sql.md) também permite selecionar os primeiros itens n no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="85e16-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="85e16-115">Uma expressão da forma:</span><span class="sxs-lookup"><span data-stu-id="85e16-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="85e16-116">`expr`como `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="85e16-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="85e16-117">Um literal ou uma expressão.</span><span class="sxs-lookup"><span data-stu-id="85e16-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e16-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="85e16-118">Remarks</span></span>  
 <span data-ttu-id="85e16-119">A cláusula SELECT é avaliada após a avaliação das cláusulas [DE](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md)e [HAVING.](having-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="85e16-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="85e16-120">A cláusula SELECT pode se referir apenas aos itens atualmente no escopo (da cláusula FROM ou de escopos externos).</span><span class="sxs-lookup"><span data-stu-id="85e16-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="85e16-121">Se uma cláusula GROUP BY tiver sido especificada, a cláusula SELECT estará autorizada apenas a referenciar os aliases das chaves GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="85e16-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="85e16-122">A referência aos itens da cláusula FROM é permitida somente em funções de agregação.</span><span class="sxs-lookup"><span data-stu-id="85e16-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="85e16-123">A lista de uma ou mais expressões de consulta após a palavra-chave SELECT é conhecida como a lista de seleção, ou mais formalmente como a projeção.</span><span class="sxs-lookup"><span data-stu-id="85e16-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="85e16-124">A forma mais geral de projeção é uma única expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="85e16-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="85e16-125">Se você selecionar `member1` um `collection1`membro de uma coleção, você `member1` produzirá uma `collection1`nova coleção de todos os valores para cada objeto em , como ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="85e16-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="85e16-126">Por exemplo, `customers` se é `Customer` uma coleção `Name` de tipo `string`que tem `Name` `customers` uma propriedade que é do tipo, a seleção de irá render uma coleção de strings, como ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="85e16-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="85e16-127">Também é possível usar a sintaxe JOIN (FULL, INNER, LEFT, OUTER, ON e RIGHT).</span><span class="sxs-lookup"><span data-stu-id="85e16-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="85e16-128">ON é necessário para junções internas e não é permitido para junções cruzadas.</span><span class="sxs-lookup"><span data-stu-id="85e16-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="85e16-129">Cláusulas de seleção de linha e valor</span><span class="sxs-lookup"><span data-stu-id="85e16-129">Row and Value Select Clauses</span></span>  
 <span data-ttu-id="85e16-130">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a duas variantes da cláusula SELECT.</span><span class="sxs-lookup"><span data-stu-id="85e16-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports two variants of the SELECT clause.</span></span> <span data-ttu-id="85e16-131">A primeira variante, seleção de linha, é identificada pela palavra-chave SELECT e pode ser usada para especificar um ou mais valores que devem ser projetados. Como um invólucro de linha é adicionado implicitamente em torno dos valores retornados, o resultado da expressão de consulta é sempre um multiconjunto de linhas.</span><span class="sxs-lookup"><span data-stu-id="85e16-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="85e16-132">Cada expressão de consulta em uma seleção de linha deve especificar um alias.</span><span class="sxs-lookup"><span data-stu-id="85e16-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="85e16-133">Se nenhum alias for[!INCLUDE[esql](../../../../../../includes/esql-md.md)] especificado, tente gerar um alias usando as regras de geração de alias.</span><span class="sxs-lookup"><span data-stu-id="85e16-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="85e16-134">Outra variante da cláusula SELECT, seleção de valor, é identificada pela palavra-chave SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="85e16-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="85e16-135">Ela permite que somente um valor seja especificado, e não adiciona um wrapper de linha.</span><span class="sxs-lookup"><span data-stu-id="85e16-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="85e16-136">Uma seleção de linha sempre pode ser expressa em termos de VALUE SELECT, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="85e16-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="85e16-137">Modificadores All e Distinct</span><span class="sxs-lookup"><span data-stu-id="85e16-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="85e16-138">Ambas as variantes de SELECT no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permitem a especificação de um modificador ALL ou DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="85e16-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="85e16-139">Se o modificador DISTINCT for especificado, as duplicatas serão eliminadas da coleção gerada pela expressão de consulta (até, e inclusive, a cláusula SELECT).</span><span class="sxs-lookup"><span data-stu-id="85e16-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="85e16-140">Se o modificador ALL for especificado, nenhuma eliminação de duplicada será executada; ALL é o padrão.</span><span class="sxs-lookup"><span data-stu-id="85e16-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="85e16-141">Diferenças de Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="85e16-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="85e16-142">Diferentemente do Transact-SQL, o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte ao uso do argumento \* na cláusula SELECT.</span><span class="sxs-lookup"><span data-stu-id="85e16-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="85e16-143">Em vez disso, o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite que as consultas projetem registros inteiros referenciando aliases de coleção da cláusula FROM, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="85e16-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="85e16-144">A expressão de consulta Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] anterior é expressa da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="85e16-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="85e16-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85e16-145">Example</span></span>  
 <span data-ttu-id="85e16-146">A consulta Entity SQL a seguir usa o operador SELECT para especificar elementos a serem retornados por uma consulta.</span><span class="sxs-lookup"><span data-stu-id="85e16-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="85e16-147">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="85e16-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="85e16-148">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="85e16-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="85e16-149">Siga o procedimento em [Como: Executar uma consulta que retorna resultados do tipo estrutural](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="85e16-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="85e16-150">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="85e16-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="85e16-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="85e16-151">See also</span></span>

- [<span data-ttu-id="85e16-152">Expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="85e16-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="85e16-153">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="85e16-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="85e16-154">Início</span><span class="sxs-lookup"><span data-stu-id="85e16-154">TOP</span></span>](top-entity-sql.md)
