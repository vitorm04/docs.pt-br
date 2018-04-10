---
title: Cláusula Where (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="baa48-102">Cláusula Where (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baa48-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="baa48-103">Especifica a condição de filtragem para uma consulta.</span><span class="sxs-lookup"><span data-stu-id="baa48-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="baa48-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="baa48-105">Partes</span><span class="sxs-lookup"><span data-stu-id="baa48-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="baa48-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="baa48-106">Required.</span></span> <span data-ttu-id="baa48-107">Uma expressão que determina se os valores para o item atual na coleção são incluídos na coleção de saída.</span><span class="sxs-lookup"><span data-stu-id="baa48-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="baa48-108">A expressão deve ser avaliada como um `Boolean` valor ou o equivalente de uma `Boolean` valor.</span><span class="sxs-lookup"><span data-stu-id="baa48-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="baa48-109">Se a condição for avaliada como `True`, o elemento é incluído no resultado da consulta; caso contrário, o elemento é excluído do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="baa48-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baa48-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="baa48-110">Remarks</span></span>  
 <span data-ttu-id="baa48-111">O `Where` cláusula permite que você filtre dados da consulta selecionando apenas os elementos que atendam a certos critérios.</span><span class="sxs-lookup"><span data-stu-id="baa48-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="baa48-112">Elementos cujos valores fazem com que o `Where` cláusula para avaliar a `True` são incluídos no resultado da consulta; outros elementos serão excluídos.</span><span class="sxs-lookup"><span data-stu-id="baa48-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="baa48-113">A expressão que é usada em uma `Where` cláusula deve ser avaliada como um `Boolean` ou o equivalente de um `Boolean`, como um número inteiro que é avaliada como `False` quando seu valor é zero.</span><span class="sxs-lookup"><span data-stu-id="baa48-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="baa48-114">Você pode combinar várias expressões em uma `Where` cláusula usando operadores lógicos, como `And`, `Or`, `AndAlso`, `OrElse`, `Is`, e `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="baa48-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="baa48-115">Por padrão, expressões de consulta não são avaliadas até que sejam acessadas — por exemplo, quando eles são associados a dados ou repetidas através de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="baa48-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="baa48-116">Como resultado, o `Where` cláusula não é avaliada até que a consulta seja acessada.</span><span class="sxs-lookup"><span data-stu-id="baa48-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="baa48-117">Se você tiver valores externos a consulta que são usados no `Where` cláusula, certifique-se de que o valor apropriado é usado no `Where` cláusula no momento em que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="baa48-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="baa48-118">Para obter mais informações sobre a execução da consulta, consulte [gravar sua consulta LINQ primeiro](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="baa48-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="baa48-119">Você pode chamar funções em um `Where` cláusula para executar um cálculo ou operação em um valor do elemento atual na coleção.</span><span class="sxs-lookup"><span data-stu-id="baa48-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="baa48-120">Chamando uma função em um `Where` cláusula pode fazer com que a consulta a ser executada imediatamente quando ele é definido em vez de quando ele é acessado.</span><span class="sxs-lookup"><span data-stu-id="baa48-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="baa48-121">Para obter mais informações sobre a execução da consulta, consulte [gravar sua consulta LINQ primeiro](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="baa48-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa48-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="baa48-122">Example</span></span>  
 <span data-ttu-id="baa48-123">A consulta a seguir usa expressões um `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção.</span><span class="sxs-lookup"><span data-stu-id="baa48-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="baa48-124">O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada.</span><span class="sxs-lookup"><span data-stu-id="baa48-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="baa48-125">O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="baa48-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="baa48-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="baa48-126">Example</span></span>  
 <span data-ttu-id="baa48-127">O exemplo a seguir usa `And` e `Or` operadores lógicos no `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="baa48-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="baa48-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baa48-128">See Also</span></span>  
 [<span data-ttu-id="baa48-129">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="baa48-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="baa48-130">Consultas</span><span class="sxs-lookup"><span data-stu-id="baa48-130">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="baa48-131">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="baa48-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="baa48-132">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="baa48-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="baa48-133">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="baa48-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
