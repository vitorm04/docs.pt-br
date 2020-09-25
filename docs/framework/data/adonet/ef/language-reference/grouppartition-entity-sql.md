---
title: PARTIÇÃODOGRUPO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 11abebeac682fed9e3a007986bb2f5c7bdb80f16
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204470"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="0c843-102">PARTIÇÃODOGRUPO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0c843-102">GROUPPARTITION (Entity SQL)</span></span>

<span data-ttu-id="0c843-103">Retorna uma coleção de valores de argumento que são projetados fora do partição atual do grupo que a agregação está relacionada.</span><span class="sxs-lookup"><span data-stu-id="0c843-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="0c843-104">A agregação de `GroupPartition` é uma agregação grupo- base e não tem nenhum formulário coleção com base.</span><span class="sxs-lookup"><span data-stu-id="0c843-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c843-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c843-105">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c843-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="0c843-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="0c843-107">Qualquer expressão de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0c843-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c843-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c843-108">Remarks</span></span>  

 <span data-ttu-id="0c843-109">A seguinte consulta gerencia uma lista de produtos e uma coleção de linha quantidades do pedido por cada produto:</span><span class="sxs-lookup"><span data-stu-id="0c843-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="0c843-110">As duas consultas são iguais semanticamente:</span><span class="sxs-lookup"><span data-stu-id="0c843-110">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="0c843-111">O operador de `GROUPPARTITION` pode ser usado em conjunto com funções agregadas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0c843-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="0c843-112">`GROUPPARTITION` é um operador aggregate especial que contém uma referência ao conjunto agrupado de entrada.</span><span class="sxs-lookup"><span data-stu-id="0c843-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="0c843-113">Essa referência pode ser usada em qualquer lugar na consulta onde o PERTO GRUPO está no escopo.</span><span class="sxs-lookup"><span data-stu-id="0c843-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="0c843-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0c843-114">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="0c843-115">Com um regular `GROUP BY` , os resultados do agrupamento ficam ocultos.</span><span class="sxs-lookup"><span data-stu-id="0c843-115">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="0c843-116">Você pode usar os resultados em uma função agregada.</span><span class="sxs-lookup"><span data-stu-id="0c843-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="0c843-117">Para ver os resultados de agrupamento, você precisa correlacionar os resultados de agrupamento e de entrada definidos usando um subconsulta.</span><span class="sxs-lookup"><span data-stu-id="0c843-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="0c843-118">As duas consultas são equivalentes:</span><span class="sxs-lookup"><span data-stu-id="0c843-118">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="0c843-119">Como mostrado no exemplo, o operador aggregate de GROUPPARTITION facilita obter uma referência a entrada definida após o agrupamento.</span><span class="sxs-lookup"><span data-stu-id="0c843-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="0c843-120">O operador GROUPPARTITION pode especificar qualquer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão na entrada do operador quando você usa o `expression` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0c843-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="0c843-121">Por exemplo todas as expressões da seguir de entrada a partição de grupo são válidas:</span><span class="sxs-lookup"><span data-stu-id="0c843-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="0c843-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c843-122">Example</span></span>  

 <span data-ttu-id="0c843-123">O exemplo a seguir mostra como usar a cláusula de GROUPPARTITION com o cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="0c843-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="0c843-124">O cláusula GROUP BY agrupa entidades de `SalesOrderHeader` pelo seu `Contact`.</span><span class="sxs-lookup"><span data-stu-id="0c843-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="0c843-125">A cláusula de GROUPPARTITION projetos na propriedade de `TotalDue` para cada grupo, resultando em uma coleção de decimais.</span><span class="sxs-lookup"><span data-stu-id="0c843-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
