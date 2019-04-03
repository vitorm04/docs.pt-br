---
title: Cláusula Group By (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 71e0ffc7f03a27a878aeb48eda9fbc58e5faae82
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839867"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="9a714-102">Cláusula Group By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a714-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="9a714-103">Agrupa os elementos de um resultado de consulta.</span><span class="sxs-lookup"><span data-stu-id="9a714-103">Groups the elements of a query result.</span></span> <span data-ttu-id="9a714-104">Também pode ser usado para aplicar funções de agregação a cada grupo.</span><span class="sxs-lookup"><span data-stu-id="9a714-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="9a714-105">A operação de agrupamento se baseia em uma ou mais chaves.</span><span class="sxs-lookup"><span data-stu-id="9a714-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a714-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a714-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="9a714-107">Partes</span><span class="sxs-lookup"><span data-stu-id="9a714-107">Parts</span></span>  
  
-   <span data-ttu-id="9a714-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="9a714-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="9a714-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9a714-109">Optional.</span></span> <span data-ttu-id="9a714-110">Um ou mais campos de variável de consulta ou variáveis que identificam explicitamente os campos a serem incluídos no resultado agrupado.</span><span class="sxs-lookup"><span data-stu-id="9a714-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="9a714-111">Se nenhum campo foi especificado, todos os campos de variável de consulta ou variáveis serão incluídos no resultado agrupado.</span><span class="sxs-lookup"><span data-stu-id="9a714-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="9a714-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9a714-112">Required.</span></span> <span data-ttu-id="9a714-113">Uma expressão que identifica a chave a ser usada para determinar os grupos de elementos.</span><span class="sxs-lookup"><span data-stu-id="9a714-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="9a714-114">Você pode especificar mais de uma chave para especificar uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="9a714-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="9a714-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9a714-115">Optional.</span></span> <span data-ttu-id="9a714-116">Uma ou mais chaves adicionais que são combinadas com `keyExp1` para criar uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="9a714-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="9a714-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9a714-117">Required.</span></span> <span data-ttu-id="9a714-118">Uma ou mais expressões que identificam como os grupos são agregados.</span><span class="sxs-lookup"><span data-stu-id="9a714-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="9a714-119">Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave, que pode estar em qualquer uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="9a714-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="9a714-120">- ou -</span><span class="sxs-lookup"><span data-stu-id="9a714-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="9a714-121">Você também pode incluir funções agregadas para aplicar ao grupo.</span><span class="sxs-lookup"><span data-stu-id="9a714-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a714-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a714-122">Remarks</span></span>  
 <span data-ttu-id="9a714-123">Você pode usar o `Group By` cláusula para dividir os resultados de uma consulta em grupos.</span><span class="sxs-lookup"><span data-stu-id="9a714-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="9a714-124">O agrupamento se baseia em uma chave ou uma chave composta que consiste em várias chaves.</span><span class="sxs-lookup"><span data-stu-id="9a714-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="9a714-125">Elementos que estão associados com valores de chave de correspondência são incluídos no mesmo grupo.</span><span class="sxs-lookup"><span data-stu-id="9a714-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="9a714-126">Você usa o `aggregateList` parâmetro do `Into` cláusula e o `Group` palavra-chave para identificar o nome do membro que é usado para fazer referência ao grupo.</span><span class="sxs-lookup"><span data-stu-id="9a714-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="9a714-127">Você também pode incluir funções agregadas no `Into` cláusula para computar os valores para os elementos agrupados.</span><span class="sxs-lookup"><span data-stu-id="9a714-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="9a714-128">Para obter uma lista das funções de agregação padrão, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9a714-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a714-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a714-129">Example</span></span>  
 <span data-ttu-id="9a714-130">O exemplo de código a seguir agrupa uma lista de clientes com base em sua localização (país) e fornece uma contagem dos clientes em cada grupo.</span><span class="sxs-lookup"><span data-stu-id="9a714-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="9a714-131">Os resultados são ordenados pelo nome de país.</span><span class="sxs-lookup"><span data-stu-id="9a714-131">The results are ordered by country name.</span></span> <span data-ttu-id="9a714-132">Os resultados agrupados são ordenados pelo nome da cidade.</span><span class="sxs-lookup"><span data-stu-id="9a714-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="9a714-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a714-133">See also</span></span>

- [<span data-ttu-id="9a714-134">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a714-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9a714-135">Consultas</span><span class="sxs-lookup"><span data-stu-id="9a714-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="9a714-136">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="9a714-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="9a714-137">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="9a714-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="9a714-138">Cláusula Order By</span><span class="sxs-lookup"><span data-stu-id="9a714-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="9a714-139">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="9a714-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="9a714-140">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="9a714-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
