---
title: "Cláusula Group By (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b719bfa2ebe4c324acf82a03e215e481283845fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="b7522-102">Cláusula Group By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7522-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="b7522-103">Agrupa os elementos de um resultado de consulta.</span><span class="sxs-lookup"><span data-stu-id="b7522-103">Groups the elements of a query result.</span></span> <span data-ttu-id="b7522-104">Também pode ser usado para aplicar funções de agregação para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="b7522-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="b7522-105">A operação de agrupamento é baseada em uma ou mais chaves.</span><span class="sxs-lookup"><span data-stu-id="b7522-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7522-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7522-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="b7522-107">Partes</span><span class="sxs-lookup"><span data-stu-id="b7522-107">Parts</span></span>  
  
-   <span data-ttu-id="b7522-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="b7522-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="b7522-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b7522-109">Optional.</span></span> <span data-ttu-id="b7522-110">Um ou mais campos de variável de consulta ou variáveis que identificam explicitamente os campos a serem incluídos no resultado agrupado.</span><span class="sxs-lookup"><span data-stu-id="b7522-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="b7522-111">Se nenhum campo foi especificado, todos os campos de variável de consulta ou variáveis são incluídos no resultado agrupado.</span><span class="sxs-lookup"><span data-stu-id="b7522-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="b7522-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b7522-112">Required.</span></span> <span data-ttu-id="b7522-113">Uma expressão que identifica a chave a ser usado para determinar os grupos de elementos.</span><span class="sxs-lookup"><span data-stu-id="b7522-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="b7522-114">Você pode especificar mais de uma chave para especificar uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="b7522-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="b7522-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b7522-115">Optional.</span></span> <span data-ttu-id="b7522-116">Uma ou mais chaves adicionais que são combinadas com `keyExp1` para criar uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="b7522-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="b7522-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b7522-117">Required.</span></span> <span data-ttu-id="b7522-118">Uma ou mais expressões que identificam como os grupos são agregados.</span><span class="sxs-lookup"><span data-stu-id="b7522-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="b7522-119">Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave, que pode ser qualquer um dos seguintes formulários:</span><span class="sxs-lookup"><span data-stu-id="b7522-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="b7522-120">-ou-</span><span class="sxs-lookup"><span data-stu-id="b7522-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="b7522-121">Você também pode incluir funções agregadas para aplicar ao grupo.</span><span class="sxs-lookup"><span data-stu-id="b7522-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7522-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7522-122">Remarks</span></span>  
 <span data-ttu-id="b7522-123">Você pode usar o `Group By` cláusula para dividir os resultados de uma consulta em grupos.</span><span class="sxs-lookup"><span data-stu-id="b7522-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="b7522-124">O agrupamento é baseado em uma chave ou uma chave composta que consiste em várias chaves.</span><span class="sxs-lookup"><span data-stu-id="b7522-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="b7522-125">Elementos que estão associados com valores de chave correspondentes são incluídos no mesmo grupo.</span><span class="sxs-lookup"><span data-stu-id="b7522-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="b7522-126">Usar o `aggregateList` parâmetro o `Into` cláusula e o `Group` palavra-chave para identificar o nome do membro que é usado para fazer referência ao grupo.</span><span class="sxs-lookup"><span data-stu-id="b7522-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="b7522-127">Você também pode incluir funções agregadas a `Into` cláusula para calcular valores para os elementos agrupados.</span><span class="sxs-lookup"><span data-stu-id="b7522-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="b7522-128">Para obter uma lista de funções de agregação padrão, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b7522-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7522-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7522-129">Example</span></span>  
 <span data-ttu-id="b7522-130">O exemplo de código a seguir agrupa uma lista de clientes com base em sua localização (país) e fornece uma contagem de clientes em cada grupo.</span><span class="sxs-lookup"><span data-stu-id="b7522-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="b7522-131">Os resultados são ordenados pelo nome de país.</span><span class="sxs-lookup"><span data-stu-id="b7522-131">The results are ordered by country name.</span></span> <span data-ttu-id="b7522-132">Os resultados agrupados são ordenados pelo nome da cidade.</span><span class="sxs-lookup"><span data-stu-id="b7522-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b7522-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7522-133">See Also</span></span>  
 [<span data-ttu-id="b7522-134">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7522-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="b7522-135">Consultas</span><span class="sxs-lookup"><span data-stu-id="b7522-135">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="b7522-136">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="b7522-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="b7522-137">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="b7522-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="b7522-138">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="b7522-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="b7522-139">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="b7522-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="b7522-140">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="b7522-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
