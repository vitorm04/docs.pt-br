---
title: TENDO (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bfa8b49b486b2bc20009874562c42ec92aa538d1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="having-entity-sql"></a><span data-ttu-id="096d8-102">TENDO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="096d8-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="096d8-103">Especifica um critério de pesquisa para um grupo ou uma agregação.</span><span class="sxs-lookup"><span data-stu-id="096d8-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="096d8-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="096d8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="096d8-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="096d8-106">Especifica o critério de pesquisa para o grupo ou a agregação encontre-se.</span><span class="sxs-lookup"><span data-stu-id="096d8-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="096d8-107">Quando HAVING foi usado com GROUP BY ALL, a cláusula HAVING substitui ALL.</span><span class="sxs-lookup"><span data-stu-id="096d8-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="096d8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="096d8-108">Remarks</span></span>  
 <span data-ttu-id="096d8-109">A cláusula HAVING é usada para especificar uma condição adicional de filtragem no resultado de um agrupamento.</span><span class="sxs-lookup"><span data-stu-id="096d8-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="096d8-110">Se nenhum GRUPO é especificado pela cláusula a expressão de consulta, um único grupo implícito definido será adotado.</span><span class="sxs-lookup"><span data-stu-id="096d8-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="096d8-111">HAVING pode ser usado apenas com o [selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="096d8-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="096d8-112">Quando [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) não é usado, HAVING se comporta como uma cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="096d8-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="096d8-113">A cláusula HAVING funciona como a cláusula WHERE exceto que são aplicados após a operação GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="096d8-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="096d8-114">Isso significa que a cláusula HAVING só pode fazer referências a agrupar alias e agregados, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="096d8-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="096d8-115">O anterior restringe os grupos somente aquelas que incluem mais de um produto.</span><span class="sxs-lookup"><span data-stu-id="096d8-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="096d8-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="096d8-116">Example</span></span>  
 <span data-ttu-id="096d8-117">A seguinte consulta SQL Entity usa HAVING e o GROUP BY operadores especificar um critério de pesquisa para um grupo ou uma agregação.</span><span class="sxs-lookup"><span data-stu-id="096d8-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="096d8-118">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="096d8-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="096d8-119">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="096d8-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="096d8-120">Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="096d8-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="096d8-121">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="096d8-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="096d8-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="096d8-122">See Also</span></span>  
 [<span data-ttu-id="096d8-123">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="096d8-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="096d8-124">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="096d8-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
