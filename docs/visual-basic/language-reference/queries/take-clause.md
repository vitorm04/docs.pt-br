---
title: Cláusula Take (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: cb109eaf43fee19b77ac690492b85919c9d78301
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816948"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="eb375-102">Cláusula Take (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb375-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="eb375-103">Retorna um número especificado de elementos contíguos do início de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="eb375-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb375-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb375-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="eb375-105">Partes</span><span class="sxs-lookup"><span data-stu-id="eb375-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="eb375-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="eb375-106">Required.</span></span> <span data-ttu-id="eb375-107">Um valor ou uma expressão que é avaliada como o número de elementos da sequência a retornar.</span><span class="sxs-lookup"><span data-stu-id="eb375-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb375-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb375-108">Remarks</span></span>  
 <span data-ttu-id="eb375-109">O `Take` cláusula faz com que uma consulta incluir um número especificado de elementos contíguos do início de uma lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="eb375-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="eb375-110">O número de elementos para incluir é especificado pelo `count` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="eb375-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="eb375-111">Você pode usar o `Take` cláusula com o `Skip` cláusula para retornar um intervalo de dados de qualquer segmento de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="eb375-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="eb375-112">Para fazer isso, passe o índice do primeiro elemento do intervalo para o `Skip` cláusula e o tamanho do intervalo para o `Take` cláusula.</span><span class="sxs-lookup"><span data-stu-id="eb375-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="eb375-113">Nesse caso, o `Take` cláusula deve ser especificada após o `Skip` cláusula.</span><span class="sxs-lookup"><span data-stu-id="eb375-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="eb375-114">Quando você usa o `Take` cláusula em uma consulta, você também precisará garantir que os resultados são retornados em uma ordem que permitirá que o `Take` cláusula para incluir os resultados pretendidos.</span><span class="sxs-lookup"><span data-stu-id="eb375-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="eb375-115">Para obter mais informações sobre a ordenação de resultados da consulta, consulte [cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="eb375-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="eb375-116">Você pode usar o `TakeWhile` cláusula para especificar que somente determinados elementos ser retornado, dependendo de uma condição fornecida.</span><span class="sxs-lookup"><span data-stu-id="eb375-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb375-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb375-117">Example</span></span>  
 <span data-ttu-id="eb375-118">O seguinte exemplo de código usa o `Take` cláusula junto com o `Skip` cláusula para retornar dados de uma consulta em páginas.</span><span class="sxs-lookup"><span data-stu-id="eb375-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="eb375-119">A função GetCustomers usa a `Skip` cláusula para ignorar os clientes na lista até que o de índice inicial fornecido valor e usa o `Take` cláusula para retornar uma página de clientes a partir desse valor de índice.</span><span class="sxs-lookup"><span data-stu-id="eb375-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="eb375-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb375-120">See also</span></span>

- [<span data-ttu-id="eb375-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb375-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="eb375-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="eb375-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="eb375-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="eb375-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="eb375-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="eb375-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="eb375-125">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="eb375-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="eb375-126">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="eb375-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="eb375-127">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="eb375-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
