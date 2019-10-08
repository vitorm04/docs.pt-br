---
title: Cláusula Skip (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004771"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="45920-102">Cláusula Skip (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45920-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="45920-103">Ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="45920-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45920-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45920-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="45920-105">Partes</span><span class="sxs-lookup"><span data-stu-id="45920-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="45920-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="45920-106">Required.</span></span> <span data-ttu-id="45920-107">Um valor ou uma expressão que é avaliada como o número de elementos da sequência a serem ignorados.</span><span class="sxs-lookup"><span data-stu-id="45920-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45920-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="45920-108">Remarks</span></span>  
 <span data-ttu-id="45920-109">A cláusula `Skip` faz com que uma consulta ignore os elementos no início de uma lista de resultados e retorne os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="45920-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="45920-110">O número de elementos a serem ignorados é identificado pelo parâmetro `count`.</span><span class="sxs-lookup"><span data-stu-id="45920-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="45920-111">Você pode usar a cláusula `Skip` com a cláusula `Take` para retornar um intervalo de dados de qualquer segmento de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="45920-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="45920-112">Para fazer isso, passe o índice do primeiro elemento do intervalo para a cláusula `Skip` e o tamanho do intervalo para a cláusula `Take`.</span><span class="sxs-lookup"><span data-stu-id="45920-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="45920-113">Quando você usa a cláusula `Skip` em uma consulta, também pode ser necessário garantir que os resultados sejam retornados em uma ordem que permitirá que a cláusula `Skip` ignore os resultados pretendidos.</span><span class="sxs-lookup"><span data-stu-id="45920-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="45920-114">Para obter mais informações sobre como ordenar os resultados da consulta, consulte [cláusula order by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="45920-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="45920-115">Você pode usar a cláusula `SkipWhile` para especificar que apenas determinados elementos sejam ignorados, dependendo de uma condição fornecida.</span><span class="sxs-lookup"><span data-stu-id="45920-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45920-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45920-116">Example</span></span>  
 <span data-ttu-id="45920-117">O exemplo de código a seguir usa a cláusula `Skip` junto com a cláusula `Take` para retornar dados de uma consulta em páginas.</span><span class="sxs-lookup"><span data-stu-id="45920-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="45920-118">A função `GetCustomers` usa a cláusula `Skip` para ignorar os clientes na lista até o valor de índice inicial fornecido e usa a cláusula `Take` para retornar uma página de clientes que inicia com esse valor de índice.</span><span class="sxs-lookup"><span data-stu-id="45920-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="45920-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45920-119">See also</span></span>

- [<span data-ttu-id="45920-120">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45920-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="45920-121">Consultas</span><span class="sxs-lookup"><span data-stu-id="45920-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="45920-122">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="45920-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="45920-123">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="45920-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="45920-124">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="45920-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="45920-125">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="45920-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="45920-126">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="45920-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
