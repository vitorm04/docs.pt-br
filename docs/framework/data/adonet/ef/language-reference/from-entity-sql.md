---
title: DE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 115fb8dfef46c74837d774012babdef9db915341
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="from-entity-sql"></a><span data-ttu-id="e3e94-102">DE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e3e94-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="e3e94-103">Especifica a coleção usada em [selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instruções.</span><span class="sxs-lookup"><span data-stu-id="e3e94-103">Specifies the collection used in [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3e94-104">Syntax</span></span>  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a><span data-ttu-id="e3e94-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e3e94-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e3e94-106">Qualquer expressão de consulta válida que produzir uma coleção para usar como uma fonte em uma instrução de `SELECT` .</span><span class="sxs-lookup"><span data-stu-id="e3e94-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3e94-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3e94-107">Remarks</span></span>  
 <span data-ttu-id="e3e94-108">Uma cláusula de `FROM` é uma lista separada por vírgulas de um ou mais itens da cláusula de `FROM` .</span><span class="sxs-lookup"><span data-stu-id="e3e94-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="e3e94-109">A cláusula de `FROM` pode ser usada para especificar uma ou mais fontes para uma declaração de `SELECT` .</span><span class="sxs-lookup"><span data-stu-id="e3e94-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="e3e94-110">A forma mais simples de uma cláusula de `FROM` é uma única expressão de consulta que identifica uma coleção e um alias usadas como a origem em uma instrução de `SELECT` , conforme ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3e94-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a><span data-ttu-id="e3e94-111">Itens de cláusula</span><span class="sxs-lookup"><span data-stu-id="e3e94-111">FROM Clause Items</span></span>  
 <span data-ttu-id="e3e94-112">Cada item de cláusula de `FROM` refere-se a uma coleção de origem na consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e3e94-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e3e94-113"> suporta as seguintes classes de itens de cláusula de `FROM` : itens simples de cláusula de `FROM` , itens de cláusula de `JOIN FROM` , e itens da cláusula de `APPLY FROM` .</span><span class="sxs-lookup"><span data-stu-id="e3e94-113"> supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="e3e94-114">Cada um desses itens de cláusula de `FROM` é descrito em detalhes nas seções seguintes.</span><span class="sxs-lookup"><span data-stu-id="e3e94-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>  
  
### <a name="simple-from-clause-item"></a><span data-ttu-id="e3e94-115">Simples de item da cláusula</span><span class="sxs-lookup"><span data-stu-id="e3e94-115">Simple FROM Clause Item</span></span>  
 <span data-ttu-id="e3e94-116">O item mais simples de cláusula de `FROM` é uma única expressão que identifica uma coleção e um alias.</span><span class="sxs-lookup"><span data-stu-id="e3e94-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="e3e94-117">A expressão pode ser simplesmente um conjunto de entidades, ou um subconsulta, ou qualquer outra expressão que é um tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="e3e94-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="e3e94-118">A seguir está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="e3e94-118">The following is an example:</span></span>  
  
```  
LOB.Customers as c  
```  
  
 <span data-ttu-id="e3e94-119">A especificação do alias é opcional.</span><span class="sxs-lookup"><span data-stu-id="e3e94-119">The alias specification is optional.</span></span> <span data-ttu-id="e3e94-120">Uma especificação alternativa de acima do item da cláusula pode ser a seguinte:</span><span class="sxs-lookup"><span data-stu-id="e3e94-120">An alternate specification of the above from clause item could be the following:</span></span>  
  
```  
LOB.Customers  
```  
  
 <span data-ttu-id="e3e94-121">Se nenhum alias for especificada, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta gerar um alias com base na expressão de coleção.</span><span class="sxs-lookup"><span data-stu-id="e3e94-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>  
  
### <a name="join-from-clause-item"></a><span data-ttu-id="e3e94-122">JUNTE-SE de item da cláusula</span><span class="sxs-lookup"><span data-stu-id="e3e94-122">JOIN FROM Clause Item</span></span>  
 <span data-ttu-id="e3e94-123">Um item da cláusula de `JOIN FROM` representa uma associação entre dois itens a cláusula de `FROM` .</span><span class="sxs-lookup"><span data-stu-id="e3e94-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> <span data-ttu-id="e3e94-124">a cruz de suporte de[!INCLUDE[esql](../../../../../../includes/esql-md.md)] join, interno join, a esquerda e certeza externo join, e externo completo join.</span><span class="sxs-lookup"><span data-stu-id="e3e94-124">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="e3e94-125">Todos esses se associam são semelhantes suporte à maneira que são suportados em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3e94-125">All these joins are supported similar to the way that they are supported in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e3e94-126">Como em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], os dois itens a cláusula de `FROM` envolvidos em `JOIN` devem ser independentes.</span><span class="sxs-lookup"><span data-stu-id="e3e94-126">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="e3e94-127">Isto é, não podem ser correlacionados.</span><span class="sxs-lookup"><span data-stu-id="e3e94-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="e3e94-128">`CROSS APPLY` ou `OUTER APPLY` podem ser usados para esses casos.</span><span class="sxs-lookup"><span data-stu-id="e3e94-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>  
  
#### <a name="cross-joins"></a><span data-ttu-id="e3e94-129">Cruzam A adição</span><span class="sxs-lookup"><span data-stu-id="e3e94-129">Cross Joins</span></span>  
 <span data-ttu-id="e3e94-130">Uma expressão de consulta de `CROSS JOIN` gerencia o produto cartesiano das duas coleções, como ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3e94-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a><span data-ttu-id="e3e94-131">Interno join</span><span class="sxs-lookup"><span data-stu-id="e3e94-131">Inner Joins</span></span>  
 <span data-ttu-id="e3e94-132">`INNER JOIN` gerencia um produto cartesiano restrito das duas coleções, como ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3e94-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 <span data-ttu-id="e3e94-133">A expressão de consulta anterior processa uma combinação de cada elemento da coleção à esquerda emparelhado com cada elemento da coleção à direita, onde a condição de `ON` é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="e3e94-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="e3e94-134">Se nenhuma condição de `ON` for especificada, `INNER JOIN` degenerado a `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="e3e94-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="e3e94-135">Left outer join e externo direito join</span><span class="sxs-lookup"><span data-stu-id="e3e94-135">Left Outer Joins and Right Outer Joins</span></span>  
 <span data-ttu-id="e3e94-136">Uma expressão de consulta de `OUTER JOIN` gerencia um produto cartesiano restrito das duas coleções, como ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3e94-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="e3e94-137">A expressão de consulta anterior processa uma combinação de cada elemento da coleção à esquerda emparelhado com cada elemento da coleção à direita, onde a condição de `ON` é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="e3e94-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="e3e94-138">Se a condição de `ON` for falsa, a expressão ainda processa uma única instância do elemento à esquerda emparelhado contra o elemento à direita, com o valor de zero.</span><span class="sxs-lookup"><span data-stu-id="e3e94-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>  
  
 <span data-ttu-id="e3e94-139">`RIGHT OUTER JOIN` pode ser expresso de maneira similar.</span><span class="sxs-lookup"><span data-stu-id="e3e94-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>  
  
#### <a name="full-outer-joins"></a><span data-ttu-id="e3e94-140">Externo completo join</span><span class="sxs-lookup"><span data-stu-id="e3e94-140">Full Outer Joins</span></span>  
 <span data-ttu-id="e3e94-141">`FULL OUTER JOIN` explícito gerencia um produto cartesiano restrito das duas coleções como ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3e94-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="e3e94-142">A expressão de consulta anterior processa uma combinação de cada elemento da coleção à esquerda emparelhado com cada elemento da coleção à direita, onde a condição de `ON` é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="e3e94-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="e3e94-143">Se a condição de `ON` for falsa, a expressão ainda processa uma instância do elemento à esquerda emparelhado contra o elemento à direita, com o valor de zero.</span><span class="sxs-lookup"><span data-stu-id="e3e94-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="e3e94-144">Também processa uma instância do elemento à direita emparelhado contra o elemento à esquerda, com o valor de zero.</span><span class="sxs-lookup"><span data-stu-id="e3e94-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3e94-145">Para preservar compatibilidade com SQL-92, em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] a palavra-chave OUTER é opcional.</span><span class="sxs-lookup"><span data-stu-id="e3e94-145">To preserve compatibility with SQL-92, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] the OUTER keyword is optional.</span></span> <span data-ttu-id="e3e94-146">Portanto, `LEFT JOIN`, `RIGHT JOIN`, e `FULL JOIN` são sinônimos para `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, e `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="e3e94-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>  
  
### <a name="apply-clause-item"></a><span data-ttu-id="e3e94-147">APPLY o item da cláusula</span><span class="sxs-lookup"><span data-stu-id="e3e94-147">APPLY Clause Item</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e3e94-148"> suporta dois tipos de `APPLY`: `CROSS APPLY` e `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="e3e94-148"> supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>  
  
 <span data-ttu-id="e3e94-149">`CROSS APPLY` gerencia um emparelhamento exclusivo de cada elemento da coleção à esquerda com um elemento da coleção gerada avaliando a expressão à direita.</span><span class="sxs-lookup"><span data-stu-id="e3e94-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="e3e94-150">Com `CROSS APPLY`, a expressão à direita funcional é dependente no elemento à esquerda, conforme ilustrado no exemplo associado de coleção:</span><span class="sxs-lookup"><span data-stu-id="e3e94-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 <span data-ttu-id="e3e94-151">O comportamento de `CROSS APPLY` é semelhante à lista de associação.</span><span class="sxs-lookup"><span data-stu-id="e3e94-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="e3e94-152">Se a expressão à direita é avaliada como uma coleção vazia, `CROSS APPLY` não gerencia nenhum pairings para essa instância do elemento à esquerda.</span><span class="sxs-lookup"><span data-stu-id="e3e94-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>  
  
 <span data-ttu-id="e3e94-153">`OUTER APPLY` é semelhante a `CROSS APPLY`, a não ser que um emparelhamento ainda é gerado mesmo quando a expressão à direita é avaliada como uma coleção vazia.</span><span class="sxs-lookup"><span data-stu-id="e3e94-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="e3e94-154">O código a seguir é um exemplo de `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="e3e94-154">The following is an example of an `OUTER APPLY`:</span></span>  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  <span data-ttu-id="e3e94-155">Ao contrário em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], não há necessidade de uma etapa para mais unnest explícita em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3e94-155">Unlike in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3e94-156">`CROSS` e operadores de `OUTER APPLY` foram introduzidos em [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3e94-156">`CROSS` and `OUTER APPLY` operators were introduced in [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="e3e94-157">Em alguns casos, o canal de consulta pode gerar Transact-SQL que contém `CROSS APPLY` e/ou operadores de `OUTER APPLY` .</span><span class="sxs-lookup"><span data-stu-id="e3e94-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="e3e94-158">Porque alguns provedores backend, incluindo versões de [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] anteriores de [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], não suportam esses operadores, essas consultas podem não ser executadas nesses provedores backend.</span><span class="sxs-lookup"><span data-stu-id="e3e94-158">Because some backend providers, including versions of [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
>   
>  <span data-ttu-id="e3e94-159">Alguns cenários típicos que podem resultar na presença de `CROSS APPLY` e/ou operadores de `OUTER APPLY` na saída consulte são os seguintes: um subconsulta correlacionado com paginação; AnyElement sobre um subconsulta correlacionado ou em uma coleção gerada por navegação; LINQ consulta que uso que agrupa os métodos que aceitam um seletor do elemento; uma consulta em que `CROSS APPLY` ou `OUTER APPLY` são especificados explicitamente; uma consulta que tenha uma compilação de `DEREF` sobre uma compilação de `REF` .</span><span class="sxs-lookup"><span data-stu-id="e3e94-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>  
  
## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="e3e94-160">Várias coleções na cláusula</span><span class="sxs-lookup"><span data-stu-id="e3e94-160">Multiple Collections in the FROM Clause</span></span>  
 <span data-ttu-id="e3e94-161">A cláusula de `FROM` pode conter mais de uma coleção separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="e3e94-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="e3e94-162">Nesses casos, coleções são assumidas para ser agrupadas.</span><span class="sxs-lookup"><span data-stu-id="e3e94-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="e3e94-163">Pense nesses CRUZ como uma maneira de n- JOIN.</span><span class="sxs-lookup"><span data-stu-id="e3e94-163">Think of these as an n-way CROSS JOIN.</span></span>  
  
 <span data-ttu-id="e3e94-164">No exemplo a seguir, `C` e `D` são coleções independentes, mas `c.Names` é dependente de `C`.</span><span class="sxs-lookup"><span data-stu-id="e3e94-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 <span data-ttu-id="e3e94-165">O exemplo anterior é logicamente equivalente ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3e94-165">The previous example is logically equivalent to the following example:</span></span>  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a><span data-ttu-id="e3e94-166">Correlação esquerda</span><span class="sxs-lookup"><span data-stu-id="e3e94-166">Left Correlation</span></span>  
 <span data-ttu-id="e3e94-167">Os itens na cláusula `FROM` podem se referir aos itens especificados nas cláusulas anteriores.</span><span class="sxs-lookup"><span data-stu-id="e3e94-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="e3e94-168">No exemplo a seguir, `C` e `D` coleções são independentes, mas `c.Names` é dependente em `C`:</span><span class="sxs-lookup"><span data-stu-id="e3e94-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 <span data-ttu-id="e3e94-169">Isso é logicamente equivalente a:</span><span class="sxs-lookup"><span data-stu-id="e3e94-169">This is logically equivalent to:</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a><span data-ttu-id="e3e94-170">Semântica</span><span class="sxs-lookup"><span data-stu-id="e3e94-170">Semantics</span></span>  
 <span data-ttu-id="e3e94-171">Logicamente, coleções na cláusula `FROM` são assumidas para ser parte de `n`- a cruz de maneira joins a não ser que no caso de uma maneira 1 percorrer se junte).</span><span class="sxs-lookup"><span data-stu-id="e3e94-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="e3e94-172">Alias na cláusula `FROM` são processadas esquerda para a direita, e adicionadas ao escopo atual para referência posterior.</span><span class="sxs-lookup"><span data-stu-id="e3e94-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="e3e94-173">A cláusula de `FROM` é assumida para gerar um multiset de linhas.</span><span class="sxs-lookup"><span data-stu-id="e3e94-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="e3e94-174">Haverá um campo para cada item na cláusula `FROM` que representa um único elemento do item da coleção.</span><span class="sxs-lookup"><span data-stu-id="e3e94-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>  
  
 <span data-ttu-id="e3e94-175">A cláusula de `FROM` gerencia logicamente um multiset das linhas da linha de tipo (c, d, e) onde os campos c, d, e e são considerados para ser do tipo de elemento de `C`, de `D`, e de `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="e3e94-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e3e94-176"> apresenta um alias para cada item simples de cláusula de `FROM` no escopo.</span><span class="sxs-lookup"><span data-stu-id="e3e94-176"> introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="e3e94-177">Por exemplo, o seguinte trecho da cláusula, os nomes são introduzidos no escopo c, d, e E.</span><span class="sxs-lookup"><span data-stu-id="e3e94-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 <span data-ttu-id="e3e94-178">Em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (em vez de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), a cláusula de `FROM` apresenta somente alias no escopo.</span><span class="sxs-lookup"><span data-stu-id="e3e94-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="e3e94-179">Todas as referências às colunas (propriedades) dessas coleções devem ser qualificados com o alias.</span><span class="sxs-lookup"><span data-stu-id="e3e94-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>  
  
## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="e3e94-180">Levantando chaves de consultas aninhadas</span><span class="sxs-lookup"><span data-stu-id="e3e94-180">Pulling Up Keys from Nested Queries</span></span>  
 <span data-ttu-id="e3e94-181">Determinados tipos de consultas que exigem gerar chaves de uma consulta aninhada não são suportados.</span><span class="sxs-lookup"><span data-stu-id="e3e94-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="e3e94-182">Por exemplo, a seguinte consulta é válido:</span><span class="sxs-lookup"><span data-stu-id="e3e94-182">For example, the following query is valid:</span></span>  
  
```  
select c.Orders from Customers as c   
```  
  
 <span data-ttu-id="e3e94-183">No entanto, a consulta a seguir é inválido, porque a consulta aninhada não tem nenhuma chaves:</span><span class="sxs-lookup"><span data-stu-id="e3e94-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3e94-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3e94-184">See Also</span></span>  
 [<span data-ttu-id="e3e94-185">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e3e94-185">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e3e94-186">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="e3e94-186">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="e3e94-187">Tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="e3e94-187">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
