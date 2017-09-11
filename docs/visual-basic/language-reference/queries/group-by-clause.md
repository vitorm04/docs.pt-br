---
title: "Cláusula Group By (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement
- Group By clause
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: 20
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
ms.openlocfilehash: a27e2f15e61456b2e7ac0ede81c66cdb4e8fd612
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="4c31f-102">Cláusula Group By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c31f-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="4c31f-103">Agrupa os elementos de um resultado de consulta.</span><span class="sxs-lookup"><span data-stu-id="4c31f-103">Groups the elements of a query result.</span></span> <span data-ttu-id="4c31f-104">Também pode ser usado para aplicar funções de agregação para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="4c31f-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="4c31f-105">A operação de agrupamento é baseada em uma ou mais chaves.</span><span class="sxs-lookup"><span data-stu-id="4c31f-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c31f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c31f-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="4c31f-107">Partes</span><span class="sxs-lookup"><span data-stu-id="4c31f-107">Parts</span></span>  
  
-   <span data-ttu-id="4c31f-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="4c31f-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="4c31f-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4c31f-109">Optional.</span></span> <span data-ttu-id="4c31f-110">Um ou mais campos de variável de consulta ou variáveis que identificam explicitamente os campos a serem incluídos no resultado agrupado.</span><span class="sxs-lookup"><span data-stu-id="4c31f-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="4c31f-111">Se nenhum campo for especificado, todos os campos de variável de consulta ou variáveis são incluídos no resultado agrupado.</span><span class="sxs-lookup"><span data-stu-id="4c31f-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="4c31f-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4c31f-112">Required.</span></span> <span data-ttu-id="4c31f-113">Uma expressão que identifica a chave a ser usada para determinar os grupos de elementos.</span><span class="sxs-lookup"><span data-stu-id="4c31f-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="4c31f-114">Você pode especificar mais de uma chave para especificar uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="4c31f-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="4c31f-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4c31f-115">Optional.</span></span> <span data-ttu-id="4c31f-116">Uma ou mais chaves adicionais que são combinadas com `keyExp1` para criar uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="4c31f-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="4c31f-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4c31f-117">Required.</span></span> <span data-ttu-id="4c31f-118">Uma ou mais expressões que identificam como os grupos são agregados.</span><span class="sxs-lookup"><span data-stu-id="4c31f-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="4c31f-119">Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave, que pode estar em qualquer uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="4c31f-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="4c31f-120">-ou-</span><span class="sxs-lookup"><span data-stu-id="4c31f-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="4c31f-121">Você também pode incluir funções agregadas para aplicar ao grupo.</span><span class="sxs-lookup"><span data-stu-id="4c31f-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c31f-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c31f-122">Remarks</span></span>  
 <span data-ttu-id="4c31f-123">Você pode usar o `Group By` cláusula para dividir os resultados de uma consulta em grupos.</span><span class="sxs-lookup"><span data-stu-id="4c31f-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="4c31f-124">O agrupamento se baseia em uma chave ou uma chave composta que consiste em várias chaves.</span><span class="sxs-lookup"><span data-stu-id="4c31f-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="4c31f-125">Elementos que estão associados com valores de chave correspondentes são incluídos no mesmo grupo.</span><span class="sxs-lookup"><span data-stu-id="4c31f-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="4c31f-126">Você usa o `aggregateList` parâmetro do `Into` cláusula e `Group` palavra-chave para identificar o nome do membro que é usado para fazer referência ao grupo.</span><span class="sxs-lookup"><span data-stu-id="4c31f-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="4c31f-127">Você também pode incluir funções agregadas de `Into` cláusula para calcular valores para os elementos agrupados.</span><span class="sxs-lookup"><span data-stu-id="4c31f-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="4c31f-128">Para obter uma lista de funções de agregação padrão, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4c31f-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c31f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c31f-129">Example</span></span>  
 <span data-ttu-id="4c31f-130">O exemplo de código a seguir agrupa uma lista de clientes com base em sua localização (país) e fornece uma contagem dos clientes em cada grupo.</span><span class="sxs-lookup"><span data-stu-id="4c31f-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="4c31f-131">Os resultados são ordenados pelo nome de país.</span><span class="sxs-lookup"><span data-stu-id="4c31f-131">The results are ordered by country name.</span></span> <span data-ttu-id="4c31f-132">Os resultados agrupados são ordenados pelo nome da cidade.</span><span class="sxs-lookup"><span data-stu-id="4c31f-132">The grouped results are ordered by city name.</span></span>  
  
 <span data-ttu-id="4c31f-133">[!code-vb[VbSimpleQuerySamples n º&11;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4c31f-133">[!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c31f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c31f-134">See Also</span></span>  
 <span data-ttu-id="4c31f-135">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="4c31f-135">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="4c31f-136"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="4c31f-136"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="4c31f-137"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4c31f-137"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="4c31f-138"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4c31f-138"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="4c31f-139"> [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4c31f-139"> [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="4c31f-140"> [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4c31f-140"> [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="4c31f-141"> [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="4c31f-141"> [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)</span></span>
