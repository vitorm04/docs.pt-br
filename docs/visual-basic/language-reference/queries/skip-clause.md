---
title: Cláusula Skip (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="ede85-102">Cláusula Skip (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ede85-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="ede85-103">Ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="ede85-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ede85-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="ede85-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ede85-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="ede85-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ede85-106">Required.</span></span> <span data-ttu-id="ede85-107">Um valor ou uma expressão que é avaliada como o número de elementos da sequência de ignorar.</span><span class="sxs-lookup"><span data-stu-id="ede85-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ede85-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ede85-108">Remarks</span></span>  
 <span data-ttu-id="ede85-109">O `Skip` cláusula faz com que uma consulta ignorar os elementos no início de uma lista de resultados e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="ede85-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="ede85-110">O número de elementos a serem ignorados é identificado pelo `count` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ede85-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="ede85-111">Você pode usar o `Skip` cláusula com o `Take` cláusula para retornar um intervalo de dados de qualquer segmento de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="ede85-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="ede85-112">Para fazer isso, passe o índice do primeiro elemento do intervalo para o `Skip` cláusula e o tamanho do intervalo para o `Take` cláusula.</span><span class="sxs-lookup"><span data-stu-id="ede85-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="ede85-113">Quando você usa o `Skip` cláusula em uma consulta, você também precisará garantir que os resultados são retornados em uma ordem que permitirá a `Skip` cláusula para ignorar os resultados desejados.</span><span class="sxs-lookup"><span data-stu-id="ede85-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="ede85-114">Para obter mais informações sobre a ordenação de resultados da consulta, consulte [cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ede85-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="ede85-115">Você pode usar o `SkipWhile` cláusula para especificar que somente determinados elementos são ignorados, dependendo de uma condição fornecida.</span><span class="sxs-lookup"><span data-stu-id="ede85-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ede85-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ede85-116">Example</span></span>  
 <span data-ttu-id="ede85-117">O seguinte exemplo de código usa o `Skip` cláusula junto com o `Take` cláusula para retornar dados de uma consulta em páginas.</span><span class="sxs-lookup"><span data-stu-id="ede85-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="ede85-118">O `GetCustomers` função usa o `Skip` cláusula para ignorar os clientes na lista até que o de índice inicial fornecido valor e usa o `Take` cláusula para retornar uma página de clientes a partir desse valor de índice.</span><span class="sxs-lookup"><span data-stu-id="ede85-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ede85-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ede85-119">See Also</span></span>  
 [<span data-ttu-id="ede85-120">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ede85-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="ede85-121">Consultas</span><span class="sxs-lookup"><span data-stu-id="ede85-121">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="ede85-122">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="ede85-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="ede85-123">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="ede85-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="ede85-124">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="ede85-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="ede85-125">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="ede85-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="ede85-126">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="ede85-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
