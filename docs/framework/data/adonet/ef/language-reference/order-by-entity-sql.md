---
title: ORDENAR POR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150063"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="c9b69-102">ORDENAR POR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c9b69-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="c9b69-103">Especifica a ordem de classificação usado em objetos retornados em uma instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="c9b69-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9b69-104">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9b69-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c9b69-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="c9b69-106">Qualquer expressão de consulta válida especificando uma propriedade para classificar.</span><span class="sxs-lookup"><span data-stu-id="c9b69-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="c9b69-107">Várias expressões de tipo podem ser especificadas.</span><span class="sxs-lookup"><span data-stu-id="c9b69-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="c9b69-108">A sequência das expressões de tipo na cláusula ORDER BY define a organização do conjunto de resultados classificada.</span><span class="sxs-lookup"><span data-stu-id="c9b69-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="c9b69-109">ORDENE {} collation_name</span><span class="sxs-lookup"><span data-stu-id="c9b69-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="c9b69-110">Especifica que a operação ORDER BY deve ser executada de acordo com a ordenação especificada em `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="c9b69-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="c9b69-111">COLLATE é aplicável somente para expressões de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c9b69-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="c9b69-112">ASC</span><span class="sxs-lookup"><span data-stu-id="c9b69-112">ASC</span></span>  
 <span data-ttu-id="c9b69-113">Especifica que os valores na propriedade especificada devem ser classificados na ordem crescente, o valor menor para o maior valor.</span><span class="sxs-lookup"><span data-stu-id="c9b69-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="c9b69-114">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c9b69-114">This is the default.</span></span>  
  
 <span data-ttu-id="c9b69-115">DESC</span><span class="sxs-lookup"><span data-stu-id="c9b69-115">DESC</span></span>  
 <span data-ttu-id="c9b69-116">Especifica que os valores na propriedade especificada devem ser classificados em ordem decrescente, o valor o maior o valor menor.</span><span class="sxs-lookup"><span data-stu-id="c9b69-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="c9b69-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="c9b69-117">LIMIT `n`</span></span>  
 <span data-ttu-id="c9b69-118">Somente o primeiro item de `n` serão selecionados.</span><span class="sxs-lookup"><span data-stu-id="c9b69-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="c9b69-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="c9b69-119">SKIP `n`</span></span>  
 <span data-ttu-id="c9b69-120">Ignora os primeiros itens de `n` .</span><span class="sxs-lookup"><span data-stu-id="c9b69-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9b69-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9b69-121">Remarks</span></span>  
 <span data-ttu-id="c9b69-122">A cláusula ORDER BY é aplicado logicamente o resultado da cláusula SELECT.</span><span class="sxs-lookup"><span data-stu-id="c9b69-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="c9b69-123">A cláusula ORDER BY pode referenciar itens na lista select usando seu alias.</span><span class="sxs-lookup"><span data-stu-id="c9b69-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="c9b69-124">A cláusula ORDER BY também pode referenciar outros variáveis que são atualmente em- escopo.</span><span class="sxs-lookup"><span data-stu-id="c9b69-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="c9b69-125">No entanto, se a cláusula SELECT foi especificada com um modificador DISTINCT, a cláusula ORDER BY pode apenas referenciar alias de cláusula SELECT.</span><span class="sxs-lookup"><span data-stu-id="c9b69-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="c9b69-126">Cada expressão na cláusula ORDER BY deve avaliar a qualquer tipo que pode ser comparado para desigualdade ordenada (menor que ou maior do que, e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="c9b69-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="c9b69-127">Esses tipos são geralmente primitivos escalares como números, cadeias de caracteres, e datas.</span><span class="sxs-lookup"><span data-stu-id="c9b69-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="c9b69-128">RowTypes de tipos comparáveis também é comparado ordem.</span><span class="sxs-lookup"><span data-stu-id="c9b69-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="c9b69-129">Se seu código itera através de um conjunto ordenado, exceto para uma projeção de nível superior, a saída não é garantida para ter sua ordem preservada.</span><span class="sxs-lookup"><span data-stu-id="c9b69-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="c9b69-130">Na seguinte amostra, a ordem é garantida para ser preservada:</span><span class="sxs-lookup"><span data-stu-id="c9b69-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="c9b69-131">Na consulta a seguir, o pedido da consulta aninhada é ignorado:</span><span class="sxs-lookup"><span data-stu-id="c9b69-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="c9b69-132">Para ter uma operação UNION, UNION ALL, EXCEPT, ou INTERSECT ordenada, use o padrão a seguir:</span><span class="sxs-lookup"><span data-stu-id="c9b69-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="c9b69-133">Palavras-chave restritas</span><span class="sxs-lookup"><span data-stu-id="c9b69-133">Restricted keywords</span></span>  
 <span data-ttu-id="c9b69-134">As seguintes palavras chave devem ser colocados entre aspas quando usado em uma cláusula de `ORDER BY` :</span><span class="sxs-lookup"><span data-stu-id="c9b69-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="c9b69-135">CROSS</span><span class="sxs-lookup"><span data-stu-id="c9b69-135">CROSS</span></span>  
  
- <span data-ttu-id="c9b69-136">FULL</span><span class="sxs-lookup"><span data-stu-id="c9b69-136">FULL</span></span>  
  
- <span data-ttu-id="c9b69-137">KEY</span><span class="sxs-lookup"><span data-stu-id="c9b69-137">KEY</span></span>  
  
- <span data-ttu-id="c9b69-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="c9b69-138">LEFT</span></span>  
  
- <span data-ttu-id="c9b69-139">ORDER</span><span class="sxs-lookup"><span data-stu-id="c9b69-139">ORDER</span></span>  
  
- <span data-ttu-id="c9b69-140">OUTER</span><span class="sxs-lookup"><span data-stu-id="c9b69-140">OUTER</span></span>  
  
- <span data-ttu-id="c9b69-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="c9b69-141">RIGHT</span></span>  
  
- <span data-ttu-id="c9b69-142">ROW</span><span class="sxs-lookup"><span data-stu-id="c9b69-142">ROW</span></span>  
  
- <span data-ttu-id="c9b69-143">VALUE</span><span class="sxs-lookup"><span data-stu-id="c9b69-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="c9b69-144">Ordenando consultas aninhadas</span><span class="sxs-lookup"><span data-stu-id="c9b69-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="c9b69-145">Em Entity Framework, uma expressão aninhada pode ser colocada em qualquer lugar na consulta; a ordem de uma consulta aninhada não é preservada.</span><span class="sxs-lookup"><span data-stu-id="c9b69-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="c9b69-146">A seguinte consulta ordenará os resultados pelo sobrenome:</span><span class="sxs-lookup"><span data-stu-id="c9b69-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="c9b69-147">Na consulta a seguir, o pedido da consulta aninhada é ignorado:</span><span class="sxs-lookup"><span data-stu-id="c9b69-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="c9b69-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9b69-148">Example</span></span>  
 <span data-ttu-id="c9b69-149">A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador cláusula ORDER pelo especificar ordem de classificação usado em objetos retornados em uma instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="c9b69-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="c9b69-150">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c9b69-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c9b69-151">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="c9b69-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c9b69-152">Siga o procedimento em [Como: Executar uma consulta que retorna resultados do tipo estrutural](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c9b69-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c9b69-153">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="c9b69-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="c9b69-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9b69-154">See also</span></span>

- [<span data-ttu-id="c9b69-155">Expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="c9b69-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="c9b69-156">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c9b69-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c9b69-157">Ignorar</span><span class="sxs-lookup"><span data-stu-id="c9b69-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="c9b69-158">Limite</span><span class="sxs-lookup"><span data-stu-id="c9b69-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="c9b69-159">Início</span><span class="sxs-lookup"><span data-stu-id="c9b69-159">TOP</span></span>](top-entity-sql.md)
