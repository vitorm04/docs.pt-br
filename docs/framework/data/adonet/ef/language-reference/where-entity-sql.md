---
title: ONDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 43c038e9ff0acfdeff88492aa2ca34fbf4ada94a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="where-entity-sql"></a><span data-ttu-id="0bed5-102">ONDE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0bed5-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="0bed5-103">A cláusula WHERE é aplicada diretamente após o [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="0bed5-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bed5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bed5-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0bed5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0bed5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0bed5-106">Um tipo booleano.</span><span class="sxs-lookup"><span data-stu-id="0bed5-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bed5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bed5-107">Remarks</span></span>  
 <span data-ttu-id="0bed5-108">A cláusula WHERE tem a mesma semântica que descrita para [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bed5-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0bed5-109">Restringe os objetos gerados pela expressão de consulta limitando os elementos das coleções de fonte àquelas que passam a condição.</span><span class="sxs-lookup"><span data-stu-id="0bed5-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="0bed5-110">A expressão `e` deve ter o tipo booleano.</span><span class="sxs-lookup"><span data-stu-id="0bed5-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="0bed5-111">A cláusula WHERE é aplicada diretamente após a cláusula e antes de qualquer agrupamento, ordenação, ou projeção ocorre.</span><span class="sxs-lookup"><span data-stu-id="0bed5-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="0bed5-112">Todos os nomes de elementos definidos na cláusula são visíveis para a expressão de uma cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="0bed5-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bed5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bed5-113">See Also</span></span>  
 [<span data-ttu-id="0bed5-114">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0bed5-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="0bed5-115">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="0bed5-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
