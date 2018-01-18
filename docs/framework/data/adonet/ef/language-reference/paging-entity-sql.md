---
title: "Paginação (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6398edb34a2389b113970444d98eec33f4833b93
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="paging-entity-sql"></a><span data-ttu-id="e2f9a-102">Paginação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e2f9a-102">Paging (Entity SQL)</span></span>
<span data-ttu-id="e2f9a-103">Paginação física pode ser executada usando o [ignorar](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) e [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) subcláusulas no [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-103">Physical paging can be performed by using the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="e2f9a-104">Para executar a físico paginação deterministically, você deve usar a SKIP e o LIMIT.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="e2f9a-105">Se você quiser restringir o número de linhas no resultado de uma maneira não determinsitic, você deve usar [superior](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e2f9a-105">If you only want to restrict the number of rows in the result in a non-determinsitic way, you should use [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span> <span data-ttu-id="e2f9a-106">A TOP e SKIP/LIMIT são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="e2f9a-107">Visão geral TOP</span><span class="sxs-lookup"><span data-stu-id="e2f9a-107">TOP Overview</span></span>  
 <span data-ttu-id="e2f9a-108">A cláusula SELECT pode ter uma cláusula as subjanelas TOP opcional após o modificador opcional de ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="e2f9a-109">A cláusula subpropriedades TOP especifica que apenas definir primeiro as linhas será retornado do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="e2f9a-110">Para obter mais informações, consulte [superior](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e2f9a-110">For more information, see [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="e2f9a-111">Visão geral de SKIP e de LIMIT</span><span class="sxs-lookup"><span data-stu-id="e2f9a-111">SKIP And LIMIT Overview</span></span>  
 <span data-ttu-id="e2f9a-112">A SKIP e o LIMIT são parte da cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="e2f9a-113">Se uma subpropriedades cláusula de expressão de SKIP está presente em uma cláusula ORDER BY, os resultados serão classificados de acordo com a especificação do tipo e o conjunto de resultados incluirá as fileiras a partir da linha seguinte logo após a expressão de SKIP.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="e2f9a-114">Por exemplo, a SKIP 5 ignorará as primeiras cinco linhas e retornará a sexta linha avançar.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="e2f9a-115">Se uma subcláusula de expressão LIMIT estiver presente em uma cláusula ORDER BY, a consulta será classificada de acordo com a especificação de classificação e o número de linhas resultante será restrito pela expressão LIMIT.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="e2f9a-116">Por exemplo, o LIMIT 5 restringirá o conjunto de resultados a instâncias ou cinco linhas.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="e2f9a-117">A SKIP e o LIMIT não têm que ser usados juntos; você pode usar apenas a SKIP ou apenas o LIMIT com cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="e2f9a-118">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="e2f9a-118">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e2f9a-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="e2f9a-119">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [<span data-ttu-id="e2f9a-120">LIMIT</span><span class="sxs-lookup"><span data-stu-id="e2f9a-120">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [<span data-ttu-id="e2f9a-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="e2f9a-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2f9a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2f9a-122">See Also</span></span>  
 [<span data-ttu-id="e2f9a-123">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e2f9a-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e2f9a-124">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e2f9a-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="e2f9a-125">Como: resultados da página por meio de consulta</span><span class="sxs-lookup"><span data-stu-id="e2f9a-125">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
