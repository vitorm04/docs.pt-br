---
title: Cláusula Distinct
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875275"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="b801c-102">Cláusula Distinct (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b801c-102">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="b801c-103">Restringe os valores da variável de intervalo atual para eliminar valores duplicados em cláusulas de consulta subsequentes.</span><span class="sxs-lookup"><span data-stu-id="b801c-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b801c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b801c-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="b801c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b801c-105">Remarks</span></span>  

 <span data-ttu-id="b801c-106">Você pode usar a `Distinct` cláusula para retornar uma lista de itens exclusivos.</span><span class="sxs-lookup"><span data-stu-id="b801c-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="b801c-107">A `Distinct` cláusula faz com que a consulta ignore resultados de consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="b801c-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="b801c-108">A `Distinct` cláusula aplica-se a valores duplicados para todos os campos de retorno especificados pela `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="b801c-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="b801c-109">Se nenhuma `Select` cláusula for especificada, a `Distinct` cláusula será aplicada à variável de intervalo para a consulta identificada na `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="b801c-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="b801c-110">Se a variável de intervalo não for um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se todos os membros do tipo corresponderem a um resultado de consulta existente.</span><span class="sxs-lookup"><span data-stu-id="b801c-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b801c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b801c-111">Example</span></span>  

 <span data-ttu-id="b801c-112">A expressão de consulta a seguir une uma lista de clientes e uma lista de pedidos de clientes.</span><span class="sxs-lookup"><span data-stu-id="b801c-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="b801c-113">A `Distinct` cláusula é incluída para retornar uma lista de nomes de clientes e datas de pedido exclusivos.</span><span class="sxs-lookup"><span data-stu-id="b801c-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="b801c-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b801c-114">See also</span></span>

- [<span data-ttu-id="b801c-115">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b801c-115">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b801c-116">Consultas</span><span class="sxs-lookup"><span data-stu-id="b801c-116">Queries</span></span>](index.md)
- [<span data-ttu-id="b801c-117">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="b801c-117">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="b801c-118">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="b801c-118">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="b801c-119">Cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="b801c-119">Where Clause</span></span>](where-clause.md)
