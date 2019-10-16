---
title: ONDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319179"
---
# <a name="where-entity-sql"></a><span data-ttu-id="e6325-102">ONDE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e6325-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="e6325-103">A cláusula WHERE é aplicada diretamente após a cláusula [from](from-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="e6325-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6325-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6325-104">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6325-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e6325-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e6325-106">Um tipo booleano.</span><span class="sxs-lookup"><span data-stu-id="e6325-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6325-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6325-107">Remarks</span></span>  
 <span data-ttu-id="e6325-108">A cláusula WHERE tem a mesma semântica, conforme descrito para Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="e6325-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="e6325-109">Restringe os objetos gerados pela expressão de consulta limitando os elementos das coleções de fonte àquelas que passam a condição.</span><span class="sxs-lookup"><span data-stu-id="e6325-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="e6325-110">A expressão `e` deve ter o tipo booleano.</span><span class="sxs-lookup"><span data-stu-id="e6325-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="e6325-111">A cláusula WHERE é aplicada diretamente após a cláusula e antes de qualquer agrupamento, ordenação, ou projeção ocorre.</span><span class="sxs-lookup"><span data-stu-id="e6325-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="e6325-112">Todos os nomes de elementos definidos na cláusula são visíveis para a expressão de uma cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="e6325-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6325-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6325-113">See also</span></span>

- [<span data-ttu-id="e6325-114">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e6325-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e6325-115">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="e6325-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
