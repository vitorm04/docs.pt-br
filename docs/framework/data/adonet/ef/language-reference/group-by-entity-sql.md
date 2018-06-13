---
title: AGRUPAR POR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 3b5edee08afef8418f19df433223818218ae909d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763180"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="80673-102">AGRUPAR POR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="80673-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="80673-103">Especifica os grupos no qual os objetos retornados por uma consulta ([selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expressão devem ser colocados.</span><span class="sxs-lookup"><span data-stu-id="80673-103">Specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80673-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80673-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="80673-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="80673-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="80673-106">Qualquer expressão de consulta válida em que o agrupamento for executado.</span><span class="sxs-lookup"><span data-stu-id="80673-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="80673-107">`expression` pode ser uma propriedade ou uma expressão de não agregação que referencia uma propriedade retornada pela cláusula.</span><span class="sxs-lookup"><span data-stu-id="80673-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="80673-108">Cada expressão em um cláusula GROUP BY deve ser avaliada como um tipo que pode ser comparado para igualdade.</span><span class="sxs-lookup"><span data-stu-id="80673-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="80673-109">Esses tipos são geralmente primitivos escalares como números, cadeias de caracteres, e datas.</span><span class="sxs-lookup"><span data-stu-id="80673-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="80673-110">Você não pode agrupar por uma coleção.</span><span class="sxs-lookup"><span data-stu-id="80673-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80673-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="80673-111">Remarks</span></span>  
 <span data-ttu-id="80673-112">Se as funções de agregação são incluídas na cláusula SELECT \<lista select >, GROUP BY calcula um valor resumido para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="80673-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="80673-113">Quando o GRUPO é especificado PERTO, ou cada nome de propriedade em qualquer expressão de nonaggregate na lista select deve ser incluído na lista GRUPO, ou o GROUP BY expressão deve coincidir exatamente com a expressão selecionar a lista.</span><span class="sxs-lookup"><span data-stu-id="80673-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80673-114">Se a cláusula ORDER BY não for especificado, os grupos retornados pelo cláusula GROUP BY não estão em qualquer ordem específica.</span><span class="sxs-lookup"><span data-stu-id="80673-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="80673-115">Para especificar ordem específica de dados, nós recomendamos que você sempre use a cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="80673-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="80673-116">Quando um cláusula GROUP BY é especificado, explícita ou implicitamente (por exemplo, a cláusula HAVING na consulta), o escopo atual está oculto, e um novo escopo é apresentado.</span><span class="sxs-lookup"><span data-stu-id="80673-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="80673-117">A cláusula SELECT, a cláusula HAVING, e a cláusula GROUP BY não poderão consultar os nomes de elemento especificado na cláusula.</span><span class="sxs-lookup"><span data-stu-id="80673-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="80673-118">Você só pode usar expressões elas mesmas de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="80673-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="80673-119">Para fazer isso, você pode atribuir novos nomes (alias) para cada expressão de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="80673-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="80673-120">Se nenhum alias for especificada para uma expressão de agrupamento, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta gerar um usando as regras de geração de alias, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="80673-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="80673-121">As expressões em cláusula GROUP BY não podem referir-se nomes definidos anteriormente no mesmo cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="80673-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="80673-122">Além de nomes de agrupamento, você também pode especificar agregados na cláusula SELECT, TENDO a cláusula, e a cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="80673-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="80673-123">Uma agregação contém uma expressão que é avaliada para cada elemento de grupo.</span><span class="sxs-lookup"><span data-stu-id="80673-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="80673-124">O operador aggregate reduz os valores de todas essas expressões (normalmente, mas nem sempre, em um único valor.)</span><span class="sxs-lookup"><span data-stu-id="80673-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="80673-125">A expressão aggregate pode fazer referências aos nomes de elementos visíveis originais no escopo pai, ou a alguns dos novos nomes introduzidos por cláusula GROUP BY próprio.</span><span class="sxs-lookup"><span data-stu-id="80673-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="80673-126">Embora as agregações apareçam na cláusula SELECT, TENDO a cláusula, e a cláusula GROUP BY, são avaliadas realmente no mesmo escopo que as expressões de agrupamento, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="80673-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="80673-127">Esta consulta usa o cláusula GROUP BY para gerar um relatório de custo de todos os produtos ordenados, subproduto dividido.</span><span class="sxs-lookup"><span data-stu-id="80673-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="80673-128">Ele fornece o nome `name` para o produto como parte da expressão de agrupamento e referências de nome na lista de seleção.</span><span class="sxs-lookup"><span data-stu-id="80673-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="80673-129">Ela também especifica a agregação `sum` na lista de seleção que referencia internamente o preço e quantidade da linha da ordem.</span><span class="sxs-lookup"><span data-stu-id="80673-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="80673-130">Cada GROUP BY expressão chave deve ter pelo menos uma referência ao escopo de entrada:</span><span class="sxs-lookup"><span data-stu-id="80673-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="80673-131">Para obter um exemplo de como usar GROUP BY, consulte [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="80673-131">For an example of using GROUP BY, see [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80673-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80673-132">Example</span></span>  
 <span data-ttu-id="80673-133">A seguinte consulta SQL Entity usa o GRUPO pelo operador para especificar os grupos em que os objetos são retornados por uma consulta.</span><span class="sxs-lookup"><span data-stu-id="80673-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="80673-134">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="80673-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="80673-135">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="80673-135">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="80673-136">Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="80673-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="80673-137">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="80673-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="80673-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80673-138">See Also</span></span>  
 [<span data-ttu-id="80673-139">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="80673-139">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="80673-140">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="80673-140">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
