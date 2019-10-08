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
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004797"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="472b4-102">Cláusula Distinct (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="472b4-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="472b4-103">Restringe os valores da variável de intervalo atual para eliminar valores duplicados em cláusulas de consulta subsequentes.</span><span class="sxs-lookup"><span data-stu-id="472b4-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="472b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="472b4-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="472b4-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="472b4-105">Remarks</span></span>  
 <span data-ttu-id="472b4-106">Você pode usar a cláusula `Distinct` para retornar uma lista de itens exclusivos.</span><span class="sxs-lookup"><span data-stu-id="472b4-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="472b4-107">A cláusula `Distinct` faz com que a consulta ignore resultados de consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="472b4-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="472b4-108">A cláusula `Distinct` se aplica a valores duplicados para todos os campos de retorno especificados pela cláusula `Select`.</span><span class="sxs-lookup"><span data-stu-id="472b4-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="472b4-109">Se nenhuma cláusula `Select` for especificada, a cláusula `Distinct` será aplicada à variável de intervalo para a consulta identificada na cláusula `From`.</span><span class="sxs-lookup"><span data-stu-id="472b4-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="472b4-110">Se a variável de intervalo não for um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se todos os membros do tipo corresponderem a um resultado de consulta existente.</span><span class="sxs-lookup"><span data-stu-id="472b4-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="472b4-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="472b4-111">Example</span></span>  
 <span data-ttu-id="472b4-112">A expressão de consulta a seguir une uma lista de clientes e uma lista de pedidos de clientes.</span><span class="sxs-lookup"><span data-stu-id="472b4-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="472b4-113">A cláusula `Distinct` está incluída para retornar uma lista de nomes de clientes e datas de pedido exclusivos.</span><span class="sxs-lookup"><span data-stu-id="472b4-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="472b4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="472b4-114">See also</span></span>

- [<span data-ttu-id="472b4-115">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="472b4-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="472b4-116">Consultas</span><span class="sxs-lookup"><span data-stu-id="472b4-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="472b4-117">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="472b4-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="472b4-118">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="472b4-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="472b4-119">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="472b4-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
