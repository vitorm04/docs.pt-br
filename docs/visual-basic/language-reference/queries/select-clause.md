---
title: "Cláusula Select (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySelect
dev_langs:
- VB
helpviewer_keywords:
- Select statement
- Select clause
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 21
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
ms.openlocfilehash: da7dc5f83b294636198b0e2f198757e4090e0757
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="1b63c-102">Cláusula Select (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b63c-102">Select Clause (Visual Basic)</span></span>
<span data-ttu-id="1b63c-103">Define o resultado de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="1b63c-103">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b63c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b63c-104">Syntax</span></span>  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="1b63c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1b63c-105">Parts</span></span>  
 `var1`  
 <span data-ttu-id="1b63c-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1b63c-106">Optional.</span></span> <span data-ttu-id="1b63c-107">Um alias que pode ser usado para referenciar os resultados da expressão de coluna.</span><span class="sxs-lookup"><span data-stu-id="1b63c-107">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="1b63c-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1b63c-108">Required.</span></span> <span data-ttu-id="1b63c-109">O nome do campo para retornar o resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="1b63c-109">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b63c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b63c-110">Remarks</span></span>  
 <span data-ttu-id="1b63c-111">Você pode usar o `Select` cláusula para definir os resultados retornados de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="1b63c-111">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="1b63c-112">Isso permite que você definir os membros de um novo tipo anônimo que é criado por uma consulta, ou direcionar os membros de um tipo nomeado que é retornado por uma consulta.</span><span class="sxs-lookup"><span data-stu-id="1b63c-112">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="1b63c-113">O `Select` cláusula não é necessária para uma consulta.</span><span class="sxs-lookup"><span data-stu-id="1b63c-113">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="1b63c-114">Se nenhum `Select` cláusula for especificada, a consulta retornará um tipo com base em todos os membros das variáveis de intervalo identificadas no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="1b63c-114">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="1b63c-115">Para obter mais informações, consulte [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="1b63c-115">For more information, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="1b63c-116">Quando uma consulta cria um tipo nomeado, ela retornará um resultado de tipo <xref:System.Collections.Generic.IEnumerable%601>onde `T` é do tipo criado.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="1b63c-116">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="1b63c-117">O `Select` cláusula pode referenciar qualquer variável no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="1b63c-117">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="1b63c-118">Isso inclui variáveis de intervalo identificadas no `From` cláusula (ou `From` cláusulas).</span><span class="sxs-lookup"><span data-stu-id="1b63c-118">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="1b63c-119">Ele também inclui quaisquer variáveis novas criadas com um alias, o `Aggregate`, `Let`, `Group By`, ou `Group Join` cláusulas ou variáveis de anterior `Select` cláusula na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="1b63c-119">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="1b63c-120">O `Select` cláusula também pode incluir valores estáticos.</span><span class="sxs-lookup"><span data-stu-id="1b63c-120">The `Select` clause can also include static values.</span></span> <span data-ttu-id="1b63c-121">Por exemplo, o exemplo de código a seguir mostra uma expressão de consulta no qual o `Select` cláusula define o resultado da consulta como um novo tipo anônimo com quatro membros: `ProductName`, `Price`, `Discount`, e `DiscountedPrice`.</span><span class="sxs-lookup"><span data-stu-id="1b63c-121">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="1b63c-122">O `ProductName` e `Price` os valores de membro são tirados da variável de intervalo do produto que é definido na `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1b63c-122">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="1b63c-123">O `DiscountedPrice` valor do membro é calculado no `Let` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1b63c-123">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="1b63c-124">O `Discount` membro é um valor estático.</span><span class="sxs-lookup"><span data-stu-id="1b63c-124">The `Discount` member is a static value.</span></span>  
  
 <span data-ttu-id="1b63c-125">[!code-vb[VbSimpleQuerySamples&#27;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b63c-125">[!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]</span></span>  
  
 <span data-ttu-id="1b63c-126">O `Select` cláusula introduz um novo conjunto de variáveis de intervalo para cláusulas de consulta subsequentes, e variáveis intervalo anteriores não estão mais no escopo.</span><span class="sxs-lookup"><span data-stu-id="1b63c-126">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="1b63c-127">A última `Select` cláusula em uma expressão de consulta determina o valor de retorno da consulta.</span><span class="sxs-lookup"><span data-stu-id="1b63c-127">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="1b63c-128">Por exemplo, a consulta a seguir retorna a empresa nome e a ordem de ID para cada pedido de clientes para o qual o total excede 500.</span><span class="sxs-lookup"><span data-stu-id="1b63c-128">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="1b63c-129">A primeira `Select` cláusula identifica as variáveis de intervalo para o `Where` e a segunda cláusula `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1b63c-129">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="1b63c-130">O segundo `Select` cláusula identifica os valores retornados pela consulta como um novo tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="1b63c-130">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 <span data-ttu-id="1b63c-131">[!code-vb[VbSimpleQuerySamples&#28;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b63c-131">[!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]</span></span>  
  
 <span data-ttu-id="1b63c-132">Se o `Select` cláusula identifica um único item para retornar, a expressão de consulta retorna uma coleção do tipo daquele item único.</span><span class="sxs-lookup"><span data-stu-id="1b63c-132">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="1b63c-133">Se o `Select` cláusula identifica vários itens para retornar, a expressão de consulta retorna uma coleção de um novo tipo anônimo, com base nos itens selecionados.</span><span class="sxs-lookup"><span data-stu-id="1b63c-133">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="1b63c-134">Por exemplo, as duas consultas a seguir retornam coleções de dois tipos diferentes com base no `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1b63c-134">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="1b63c-135">A primeira consulta retorna uma coleção de nomes de empresa como cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1b63c-135">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="1b63c-136">A segunda consulta retorna uma coleção de `Customer` objetos preenchidos com os nomes de empresa e informações de endereço.</span><span class="sxs-lookup"><span data-stu-id="1b63c-136">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 <span data-ttu-id="1b63c-137">[!code-vb[29 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b63c-137">[!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b63c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1b63c-138">Example</span></span>  
 <span data-ttu-id="1b63c-139">A seguinte consulta expressão utiliza um `From` cláusula para declarar uma variável de intervalo `cust` para o `customers` coleção.</span><span class="sxs-lookup"><span data-stu-id="1b63c-139">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="1b63c-140">O `Select` cláusula seleciona o nome do cliente e o valor de ID e preenche o `CompanyName` e `CustomerID` colunas da nova variável de intervalo.</span><span class="sxs-lookup"><span data-stu-id="1b63c-140">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="1b63c-141">O `For Each` instrução faz um loop sobre cada objeto retornado e exibe o `CompanyName` e `CustomerID` colunas para cada registro.</span><span class="sxs-lookup"><span data-stu-id="1b63c-141">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 <span data-ttu-id="1b63c-142">[!code-vb[30 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b63c-142">[!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b63c-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b63c-143">See Also</span></span>  
 <span data-ttu-id="1b63c-144">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="1b63c-144">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="1b63c-145"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="1b63c-145"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="1b63c-146"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="1b63c-146"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="1b63c-147"> [Onde cláusula](../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="1b63c-147"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="1b63c-148"> [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="1b63c-148"> [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="1b63c-149"> [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="1b63c-149"> [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span></span>
