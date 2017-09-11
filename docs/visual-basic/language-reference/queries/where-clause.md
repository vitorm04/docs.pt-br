---
title: "Onde cláusula (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryWhere
dev_langs:
- VB
helpviewer_keywords:
- Where statement
- queries [Visual Basic], Where
- Where clause
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5544f442bbc13c7624c2260409f69491cfc44e14
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="19437-102">Cláusula Where (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19437-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="19437-103">Especifica a condição de filtragem para uma consulta.</span><span class="sxs-lookup"><span data-stu-id="19437-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19437-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19437-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="19437-105">Partes</span><span class="sxs-lookup"><span data-stu-id="19437-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="19437-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="19437-106">Required.</span></span> <span data-ttu-id="19437-107">Uma expressão que determina se os valores para o item atual na coleção são incluídos na coleção de saída.</span><span class="sxs-lookup"><span data-stu-id="19437-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="19437-108">A expressão deve ser avaliada como um `Boolean` valor ou o equivalente de uma `Boolean` valor.</span><span class="sxs-lookup"><span data-stu-id="19437-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="19437-109">Se a condição for avaliada como `True`, o elemento é incluído no resultado da consulta; caso contrário, o elemento é excluído do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="19437-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19437-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="19437-110">Remarks</span></span>  
 <span data-ttu-id="19437-111">O `Where` cláusula permite que você filtre dados da consulta selecionando apenas os elementos que atendam a determinados critérios.</span><span class="sxs-lookup"><span data-stu-id="19437-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="19437-112">Elementos cujos valores fazem com que o `Where` cláusula para avaliar a `True` são incluídos no resultado da consulta; outros elementos serão excluídos.</span><span class="sxs-lookup"><span data-stu-id="19437-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="19437-113">A expressão que é usada em uma `Where` cláusula deve ser avaliada como um `Boolean` ou o equivalente de um `Boolean`, como um inteiro que é avaliada para `False` quando seu valor é zero.</span><span class="sxs-lookup"><span data-stu-id="19437-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="19437-114">Você pode combinar várias expressões em uma `Where` cláusula usando operadores lógicos, como `And`, `Or`, `AndAlso`, `OrElse`, `Is`, e `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="19437-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="19437-115">Por padrão, expressões de consulta não são avaliadas até que sejam acessadas — por exemplo, quando forem ligados a dados ou repetidas através de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="19437-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="19437-116">Como resultado, o `Where` cláusula não é avaliada até que a consulta seja acessada.</span><span class="sxs-lookup"><span data-stu-id="19437-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="19437-117">Se você tiver valores externos a consulta que são usados no `Where` cláusula, certifique-se de que o valor apropriado é usado no `Where` cláusula no momento em que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="19437-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="19437-118">Para obter mais informações sobre a execução da consulta, consulte [escrita Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="19437-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="19437-119">Você pode chamar funções em uma `Where` cláusula para executar um cálculo ou operação em um valor do elemento atual na coleção.</span><span class="sxs-lookup"><span data-stu-id="19437-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="19437-120">Chamar uma função em um `Where` cláusula pode fazer com que a consulta seja executada imediatamente quando ele é definido em vez de quando ele é acessado.</span><span class="sxs-lookup"><span data-stu-id="19437-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="19437-121">Para obter mais informações sobre a execução da consulta, consulte [escrita Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="19437-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19437-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19437-122">Example</span></span>  
 <span data-ttu-id="19437-123">A seguinte consulta expressão utiliza um `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção.</span><span class="sxs-lookup"><span data-stu-id="19437-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="19437-124">O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada.</span><span class="sxs-lookup"><span data-stu-id="19437-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="19437-125">O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="19437-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 <span data-ttu-id="19437-126">[!code-vb[VbSimpleQuerySamples&#23;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="19437-126">[!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="19437-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19437-127">Example</span></span>  
 <span data-ttu-id="19437-128">O exemplo a seguir usa `And` e `Or` operadores lógicos no `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="19437-128">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 <span data-ttu-id="19437-129">[!code-vb[VbSimpleQuerySamples&#31;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="19437-129">[!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19437-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19437-130">See Also</span></span>  
 <span data-ttu-id="19437-131">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="19437-131">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="19437-132"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="19437-132"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="19437-133"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="19437-133"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="19437-134"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="19437-134"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="19437-135"> [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)</span><span class="sxs-lookup"><span data-stu-id="19437-135"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md)</span></span>
