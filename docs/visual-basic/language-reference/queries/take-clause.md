---
title: Cláusula Take
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349640"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="6a16c-102">Cláusula Take (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a16c-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="6a16c-103">Returns a specified number of contiguous elements from the start of a collection.</span><span class="sxs-lookup"><span data-stu-id="6a16c-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a16c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a16c-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="6a16c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="6a16c-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="6a16c-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6a16c-106">Required.</span></span> <span data-ttu-id="6a16c-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span><span class="sxs-lookup"><span data-stu-id="6a16c-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a16c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a16c-108">Remarks</span></span>  
 <span data-ttu-id="6a16c-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span><span class="sxs-lookup"><span data-stu-id="6a16c-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="6a16c-110">The number of elements to include is specified by the `count` parameter.</span><span class="sxs-lookup"><span data-stu-id="6a16c-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="6a16c-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span><span class="sxs-lookup"><span data-stu-id="6a16c-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="6a16c-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span><span class="sxs-lookup"><span data-stu-id="6a16c-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="6a16c-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span><span class="sxs-lookup"><span data-stu-id="6a16c-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="6a16c-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span><span class="sxs-lookup"><span data-stu-id="6a16c-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="6a16c-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6a16c-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="6a16c-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span><span class="sxs-lookup"><span data-stu-id="6a16c-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a16c-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a16c-117">Example</span></span>  
 <span data-ttu-id="6a16c-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span><span class="sxs-lookup"><span data-stu-id="6a16c-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="6a16c-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span><span class="sxs-lookup"><span data-stu-id="6a16c-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6a16c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a16c-120">See also</span></span>

- [<span data-ttu-id="6a16c-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a16c-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6a16c-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="6a16c-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="6a16c-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="6a16c-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="6a16c-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="6a16c-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="6a16c-125">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="6a16c-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="6a16c-126">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="6a16c-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="6a16c-127">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="6a16c-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
