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
ms.openlocfilehash: 94471898807ef4552564c3e01465f2b2f6211d0c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335374"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="3e1af-102">Cláusula Distinct (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e1af-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="3e1af-103">Restringe os valores da variável de intervalo atual para eliminar valores duplicados em cláusulas de consulta subsequentes.</span><span class="sxs-lookup"><span data-stu-id="3e1af-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e1af-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="3e1af-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e1af-105">Remarks</span></span>  
 <span data-ttu-id="3e1af-106">Você pode usar a cláusula `Distinct` para retornar uma lista de itens exclusivos.</span><span class="sxs-lookup"><span data-stu-id="3e1af-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="3e1af-107">A cláusula `Distinct` faz com que a consulta ignore resultados de consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="3e1af-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="3e1af-108">A cláusula `Distinct` se aplica a valores duplicados para todos os campos de retorno especificados pela cláusula `Select`.</span><span class="sxs-lookup"><span data-stu-id="3e1af-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="3e1af-109">Se nenhuma cláusula de `Select` for especificada, a cláusula `Distinct` será aplicada à variável de intervalo para a consulta identificada na cláusula `From`.</span><span class="sxs-lookup"><span data-stu-id="3e1af-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="3e1af-110">Se a variável de intervalo não for um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se todos os membros do tipo corresponderem a um resultado de consulta existente.</span><span class="sxs-lookup"><span data-stu-id="3e1af-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e1af-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e1af-111">Example</span></span>  
 <span data-ttu-id="3e1af-112">A expressão de consulta a seguir une uma lista de clientes e uma lista de pedidos de clientes.</span><span class="sxs-lookup"><span data-stu-id="3e1af-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="3e1af-113">A cláusula `Distinct` está incluída para retornar uma lista de nomes de clientes e datas de pedido exclusivos.</span><span class="sxs-lookup"><span data-stu-id="3e1af-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="3e1af-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e1af-114">See also</span></span>

- [<span data-ttu-id="3e1af-115">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e1af-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3e1af-116">Consultas</span><span class="sxs-lookup"><span data-stu-id="3e1af-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3e1af-117">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="3e1af-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="3e1af-118">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="3e1af-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="3e1af-119">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="3e1af-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
