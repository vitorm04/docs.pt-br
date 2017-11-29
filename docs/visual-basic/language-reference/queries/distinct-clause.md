---
title: "Cláusula Distinct (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="c20a4-102">Cláusula Distinct (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c20a4-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="c20a4-103">Restringe os valores da variável de intervalo atual para eliminar valores duplicados nas cláusulas de consulta subsequentes.</span><span class="sxs-lookup"><span data-stu-id="c20a4-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c20a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c20a4-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="c20a4-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c20a4-105">Remarks</span></span>  
 <span data-ttu-id="c20a4-106">Você pode usar o `Distinct` cláusula para retornar uma lista de itens exclusivos.</span><span class="sxs-lookup"><span data-stu-id="c20a4-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="c20a4-107">O `Distinct` cláusula faz com que a consulta ignorar resultados de consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="c20a4-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="c20a4-108">O `Distinct` cláusula se aplica a valores duplicados para todos os campos especificados de retorno de `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="c20a4-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="c20a4-109">Se nenhum `Select` cláusula for especificada, o `Distinct` cláusula é aplicada à variável de intervalo para a consulta identificada no `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="c20a4-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="c20a4-110">Se a variável de intervalo não é um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se todos os membros do tipo correspondem a um resultado de consulta existente.</span><span class="sxs-lookup"><span data-stu-id="c20a4-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c20a4-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c20a4-111">Example</span></span>  
 <span data-ttu-id="c20a4-112">A expressão de consulta a seguir associa uma lista de clientes e uma lista de pedidos de clientes.</span><span class="sxs-lookup"><span data-stu-id="c20a4-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="c20a4-113">O `Distinct` cláusula é incluída para retornar uma lista de nomes exclusivos de clientes e datas de pedido.</span><span class="sxs-lookup"><span data-stu-id="c20a4-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c20a4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c20a4-114">See Also</span></span>  
 [<span data-ttu-id="c20a4-115">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c20a4-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="c20a4-116">Consultas</span><span class="sxs-lookup"><span data-stu-id="c20a4-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="c20a4-117">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="c20a4-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="c20a4-118">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="c20a4-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="c20a4-119">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="c20a4-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
