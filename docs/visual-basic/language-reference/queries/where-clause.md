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
ms.openlocfilehash: 60b7ebe96ce0c4580c36675b2e4aa5f9888732c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349624"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="7717f-102">Cláusula Where (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7717f-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="7717f-103">Especifica a condição de filtragem para uma consulta.</span><span class="sxs-lookup"><span data-stu-id="7717f-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7717f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7717f-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="7717f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="7717f-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="7717f-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="7717f-106">Required.</span></span> <span data-ttu-id="7717f-107">Uma expressão que determina se os valores para o item atual na coleção são incluídos na coleção de saída.</span><span class="sxs-lookup"><span data-stu-id="7717f-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="7717f-108">A expressão deve ser avaliada como um valor `Boolean` ou o equivalente de um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7717f-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="7717f-109">Se a condição for avaliada como `True`, o elemento será incluído no resultado da consulta; caso contrário, o elemento será excluído do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="7717f-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7717f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7717f-110">Remarks</span></span>  
 <span data-ttu-id="7717f-111">A cláusula `Where` permite filtrar dados de consulta selecionando apenas os elementos que atendem a determinados critérios.</span><span class="sxs-lookup"><span data-stu-id="7717f-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="7717f-112">Os elementos cujos valores fazem com que a cláusula de `Where` seja avaliada como `True` são incluídos no resultado da consulta; outros elementos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="7717f-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="7717f-113">A expressão usada em uma cláusula `Where` deve ser avaliada como um `Boolean` ou equivalente a um `Boolean`, como um inteiro que é avaliado como `False` quando seu valor é zero.</span><span class="sxs-lookup"><span data-stu-id="7717f-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="7717f-114">Você pode combinar várias expressões em uma cláusula `Where` usando operadores lógicos, como `And`, `Or`, `AndAlso`, `OrElse`, `Is`e `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="7717f-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="7717f-115">Por padrão, as expressões de consulta não são avaliadas até que sejam acessadas — por exemplo, quando elas são vinculadas a dados ou iteradas em um loop de `For`.</span><span class="sxs-lookup"><span data-stu-id="7717f-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="7717f-116">Como resultado, a cláusula `Where` não é avaliada até que a consulta seja acessada.</span><span class="sxs-lookup"><span data-stu-id="7717f-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="7717f-117">Se você tiver valores externos à consulta que são usados na cláusula `Where`, verifique se o valor apropriado é usado na cláusula `Where` no momento em que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="7717f-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="7717f-118">Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="7717f-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="7717f-119">Você pode chamar funções dentro de uma cláusula `Where` para executar um cálculo ou uma operação em um valor do elemento atual na coleção.</span><span class="sxs-lookup"><span data-stu-id="7717f-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="7717f-120">Chamar uma função em uma cláusula `Where` pode fazer com que a consulta seja executada imediatamente quando definida em vez de quando ela é acessada.</span><span class="sxs-lookup"><span data-stu-id="7717f-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="7717f-121">Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="7717f-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7717f-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7717f-122">Example</span></span>  
 <span data-ttu-id="7717f-123">A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalo `cust` para cada objeto `Customer` na coleção de `customers`.</span><span class="sxs-lookup"><span data-stu-id="7717f-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="7717f-124">A cláusula `Where` usa a variável Range para restringir a saída aos clientes da região especificada.</span><span class="sxs-lookup"><span data-stu-id="7717f-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="7717f-125">O loop de `For Each` exibe o nome da empresa para cada cliente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="7717f-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="7717f-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7717f-126">Example</span></span>  
 <span data-ttu-id="7717f-127">O exemplo a seguir usa `And` e `Or` operadores lógicos na cláusula `Where`.</span><span class="sxs-lookup"><span data-stu-id="7717f-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="7717f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7717f-128">See also</span></span>

- [<span data-ttu-id="7717f-129">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7717f-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7717f-130">Consultas</span><span class="sxs-lookup"><span data-stu-id="7717f-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="7717f-131">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="7717f-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="7717f-132">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="7717f-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="7717f-133">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="7717f-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
