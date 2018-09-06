---
title: Cláusula Distinct (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 18d09d8018303aab6a69801c84c7ec9c6ea19ca9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788617"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="2f3a3-102">Cláusula Distinct (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f3a3-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="2f3a3-103">Restringe os valores da variável de intervalo para eliminar valores duplicados nas cláusulas de consulta subsequentes.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f3a3-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="2f3a3-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f3a3-105">Remarks</span></span>  
 <span data-ttu-id="2f3a3-106">Você pode usar o `Distinct` cláusula para retornar uma lista de itens exclusivos.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="2f3a3-107">O `Distinct` cláusula faz com que a consulta a ignorar os resultados da consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="2f3a3-108">O `Distinct` cláusula se aplica a valores duplicados para todos os campos especificados de retorno de `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="2f3a3-109">Se nenhum `Select` cláusula for especificada, o `Distinct` cláusula é aplicada à variável de intervalo para a consulta identificada no `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="2f3a3-110">Se a variável de intervalo não é um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se correspondem a todos os membros do tipo de um resultado de consulta existente.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f3a3-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f3a3-111">Example</span></span>  
 <span data-ttu-id="2f3a3-112">A expressão de consulta a seguir une uma lista de clientes e uma lista de pedidos do cliente.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="2f3a3-113">O `Distinct` cláusula é incluída para retornar uma lista de nomes exclusivos de clientes e datas de pedido.</span><span class="sxs-lookup"><span data-stu-id="2f3a3-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2f3a3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f3a3-114">See Also</span></span>  
 [<span data-ttu-id="2f3a3-115">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f3a3-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="2f3a3-116">Consultas</span><span class="sxs-lookup"><span data-stu-id="2f3a3-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="2f3a3-117">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="2f3a3-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="2f3a3-118">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="2f3a3-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="2f3a3-119">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="2f3a3-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
