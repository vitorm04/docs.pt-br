---
title: Cláusula Where
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359535"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="460c6-102">Cláusula Where (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="460c6-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="460c6-103">Especifica a condição de filtragem para uma consulta.</span><span class="sxs-lookup"><span data-stu-id="460c6-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="460c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="460c6-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="460c6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="460c6-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="460c6-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="460c6-106">Required.</span></span> <span data-ttu-id="460c6-107">Uma expressão que determina se os valores para o item atual na coleção são incluídos na coleção de saída.</span><span class="sxs-lookup"><span data-stu-id="460c6-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="460c6-108">A expressão deve ser avaliada como um `Boolean` valor ou equivalente a um `Boolean` valor.</span><span class="sxs-lookup"><span data-stu-id="460c6-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="460c6-109">Se a condição for avaliada como `True` , o elemento será incluído no resultado da consulta; caso contrário, o elemento será excluído do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="460c6-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="460c6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="460c6-110">Remarks</span></span>  
 <span data-ttu-id="460c6-111">A `Where` cláusula permite filtrar dados de consulta selecionando apenas os elementos que atendem a determinados critérios.</span><span class="sxs-lookup"><span data-stu-id="460c6-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="460c6-112">Os elementos cujos valores fazem a `Where` cláusula ser avaliada como `True` estão incluídos no resultado da consulta; outros elementos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="460c6-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="460c6-113">A expressão usada em uma `Where` cláusula deve ser avaliada como um `Boolean` ou equivalente de um `Boolean` , como um inteiro que é avaliado como `False` quando seu valor é zero.</span><span class="sxs-lookup"><span data-stu-id="460c6-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="460c6-114">Você pode combinar várias expressões em uma `Where` cláusula usando operadores lógicos, como,,,, `And` `Or` `AndAlso` `OrElse` `Is` e `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="460c6-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="460c6-115">Por padrão, as expressões de consulta não são avaliadas até que elas sejam acessadas — por exemplo, quando elas são vinculadas a dados ou iteradas em um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="460c6-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="460c6-116">Como resultado, a `Where` cláusula não é avaliada até que a consulta seja acessada.</span><span class="sxs-lookup"><span data-stu-id="460c6-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="460c6-117">Se você tiver valores externos à consulta que são usados na `Where` cláusula, verifique se o valor apropriado é usado na `Where` cláusula no momento em que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="460c6-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="460c6-118">Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="460c6-118">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="460c6-119">Você pode chamar funções dentro de uma `Where` cláusula para executar um cálculo ou uma operação em um valor do elemento atual na coleção.</span><span class="sxs-lookup"><span data-stu-id="460c6-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="460c6-120">Chamar uma função em uma `Where` cláusula pode fazer com que a consulta seja executada imediatamente quando ela é definida em vez de quando é acessada.</span><span class="sxs-lookup"><span data-stu-id="460c6-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="460c6-121">Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="460c6-121">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="460c6-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="460c6-122">Example</span></span>  
 <span data-ttu-id="460c6-123">A expressão de consulta a seguir usa uma `From` cláusula para declarar uma variável `cust` de intervalo para cada `Customer` objeto na `customers` coleção.</span><span class="sxs-lookup"><span data-stu-id="460c6-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="460c6-124">A `Where` cláusula usa a variável Range para restringir a saída aos clientes da região especificada.</span><span class="sxs-lookup"><span data-stu-id="460c6-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="460c6-125">O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="460c6-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="460c6-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="460c6-126">Example</span></span>  
 <span data-ttu-id="460c6-127">O exemplo a seguir `And` usa `Or` os operadores lógicos e na `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="460c6-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="460c6-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="460c6-128">See also</span></span>

- [<span data-ttu-id="460c6-129">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="460c6-129">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="460c6-130">Consultas</span><span class="sxs-lookup"><span data-stu-id="460c6-130">Queries</span></span>](index.md)
- [<span data-ttu-id="460c6-131">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="460c6-131">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="460c6-132">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="460c6-132">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="460c6-133">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="460c6-133">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
