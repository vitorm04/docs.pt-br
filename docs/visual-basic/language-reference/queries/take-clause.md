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
ms.openlocfilehash: 32a4c7fd7f1e2f6fe640f3f53f15579f014759d5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004722"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="162f7-102">Cláusula Take (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="162f7-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="162f7-103">Retorna um número especificado de elementos contíguos do início de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="162f7-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="162f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="162f7-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="162f7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="162f7-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="162f7-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="162f7-106">Required.</span></span> <span data-ttu-id="162f7-107">Um valor ou uma expressão que é avaliada como o número de elementos da sequência a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="162f7-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="162f7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="162f7-108">Remarks</span></span>  
 <span data-ttu-id="162f7-109">A cláusula `Take` faz com que uma consulta inclua um número especificado de elementos contíguos do início de uma lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="162f7-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="162f7-110">O número de elementos a serem incluídos é especificado pelo parâmetro `count`.</span><span class="sxs-lookup"><span data-stu-id="162f7-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="162f7-111">Você pode usar a cláusula `Take` com a cláusula `Skip` para retornar um intervalo de dados de qualquer segmento de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="162f7-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="162f7-112">Para fazer isso, passe o índice do primeiro elemento do intervalo para a cláusula `Skip` e o tamanho do intervalo para a cláusula `Take`.</span><span class="sxs-lookup"><span data-stu-id="162f7-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="162f7-113">Nesse caso, a cláusula `Take` deve ser especificada após a cláusula `Skip`.</span><span class="sxs-lookup"><span data-stu-id="162f7-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="162f7-114">Quando você usa a cláusula `Take` em uma consulta, também pode ser necessário garantir que os resultados sejam retornados em uma ordem que permitirá que a cláusula `Take` inclua os resultados pretendidos.</span><span class="sxs-lookup"><span data-stu-id="162f7-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="162f7-115">Para obter mais informações sobre como ordenar os resultados da consulta, consulte [cláusula order by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="162f7-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="162f7-116">Você pode usar a cláusula `TakeWhile` para especificar que apenas determinados elementos sejam retornados, dependendo de uma condição fornecida.</span><span class="sxs-lookup"><span data-stu-id="162f7-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="162f7-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="162f7-117">Example</span></span>  
 <span data-ttu-id="162f7-118">O exemplo de código a seguir usa a cláusula `Take` junto com a cláusula `Skip` para retornar dados de uma consulta em páginas.</span><span class="sxs-lookup"><span data-stu-id="162f7-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="162f7-119">A função GetCustomers usa a cláusula `Skip` para ignorar os clientes na lista até o valor de índice inicial fornecido e usa a cláusula `Take` para retornar uma página de clientes que inicia com esse valor de índice.</span><span class="sxs-lookup"><span data-stu-id="162f7-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="162f7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="162f7-120">See also</span></span>

- [<span data-ttu-id="162f7-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="162f7-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="162f7-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="162f7-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="162f7-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="162f7-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="162f7-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="162f7-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="162f7-125">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="162f7-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="162f7-126">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="162f7-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="162f7-127">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="162f7-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
