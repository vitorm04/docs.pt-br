---
title: "PARTIÇÃODOGRUPO (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8807564cb9acf8c50aed43ee11441ebdfbbcea78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="01a86-102">PARTIÇÃODOGRUPO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="01a86-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="01a86-103">Retorna uma coleção de valores de argumento que são projetados fora do partição atual do grupo que a agregação está relacionada.</span><span class="sxs-lookup"><span data-stu-id="01a86-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="01a86-104">A agregação de `GroupPartition` é uma agregação grupo- base e não tem nenhum formulário coleção com base.</span><span class="sxs-lookup"><span data-stu-id="01a86-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01a86-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01a86-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="01a86-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="01a86-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="01a86-107">Qualquer expressão de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="01a86-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01a86-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="01a86-108">Remarks</span></span>  
 <span data-ttu-id="01a86-109">A seguinte consulta gerencia uma lista de produtos e uma coleção de linha quantidades do pedido por cada produto:</span><span class="sxs-lookup"><span data-stu-id="01a86-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="01a86-110">As duas consultas são iguais semanticamente:</span><span class="sxs-lookup"><span data-stu-id="01a86-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="01a86-111">O operador de `GROUPPARTITION` pode ser usado em conjunto com funções agregadas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="01a86-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="01a86-112">`GROUPPARTITION` é um operador aggregate especial que contém uma referência ao conjunto agrupado de entrada.</span><span class="sxs-lookup"><span data-stu-id="01a86-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="01a86-113">Essa referência pode ser usada em qualquer lugar na consulta onde o PERTO GRUPO está no escopo.</span><span class="sxs-lookup"><span data-stu-id="01a86-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="01a86-114">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="01a86-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="01a86-115">Com um GRUPO normal PERTO, os resultados de agrupamento são ocultos.</span><span class="sxs-lookup"><span data-stu-id="01a86-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="01a86-116">Você pode usar os resultados em uma função agregada.</span><span class="sxs-lookup"><span data-stu-id="01a86-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="01a86-117">Para ver os resultados de agrupamento, você precisa correlacionar os resultados de agrupamento e de entrada definidos usando um subconsulta.</span><span class="sxs-lookup"><span data-stu-id="01a86-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="01a86-118">As duas consultas são equivalentes:</span><span class="sxs-lookup"><span data-stu-id="01a86-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="01a86-119">Como mostrado no exemplo, o operador aggregate de GROUPPARTITION facilita obter uma referência a entrada definida após o agrupamento.</span><span class="sxs-lookup"><span data-stu-id="01a86-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="01a86-120">O operador GROUPPARTITION pode especificar qualquer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão no operador de entrada quando você usa o `expression` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="01a86-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="01a86-121">Por exemplo todas as expressões da seguir de entrada a partição de grupo são válidas:</span><span class="sxs-lookup"><span data-stu-id="01a86-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="01a86-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01a86-122">Example</span></span>  
 <span data-ttu-id="01a86-123">O exemplo a seguir mostra como usar a cláusula de GROUPPARTITION com o cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="01a86-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="01a86-124">O cláusula GROUP BY agrupa entidades de `SalesOrderHeader` pelo seu `Contact`.</span><span class="sxs-lookup"><span data-stu-id="01a86-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="01a86-125">A cláusula de GROUPPARTITION projetos na propriedade de `TotalDue` para cada grupo, resultando em uma coleção de decimais.</span><span class="sxs-lookup"><span data-stu-id="01a86-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
