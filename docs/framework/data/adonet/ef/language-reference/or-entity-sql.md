---
title: '|| (OU) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 09ae742f648f95819a8c6fc64d402c4f11c7748a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="-or-entity-sql"></a><span data-ttu-id="e9bfd-102">|| (OU) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e9bfd-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="e9bfd-103">Combina duas expressões de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="e9bfd-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9bfd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9bfd-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9bfd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9bfd-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="e9bfd-106">Qualquer expressão válida que retorna `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9bfd-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e9bfd-107">Return Value</span></span>  
 <span data-ttu-id="e9bfd-108">`true` quando uma das condições for `true`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9bfd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9bfd-109">Remarks</span></span>  
 <span data-ttu-id="e9bfd-110">OR é um operador lógico de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e9bfd-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="e9bfd-111">É usada para combinar duas condições.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-111">It is used to combine two conditions.</span></span> <span data-ttu-id="e9bfd-112">Quando mais de um operador lógico é usado em uma declaração, OU de operadores são avaliados em seguida E operadores.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="e9bfd-113">No entanto, você pode alterar a ordem de classificação usando parênteses.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="e9bfd-114">Barras verticais duplas (&#124;&#124;) têm a mesma funcionalidade que o operador OR.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="e9bfd-115">A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="e9bfd-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="e9bfd-116">TRUE</span></span>|<span data-ttu-id="e9bfd-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="e9bfd-117">TRUE</span></span>|<span data-ttu-id="e9bfd-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="e9bfd-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="e9bfd-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="e9bfd-119">TRUE</span></span>|<span data-ttu-id="e9bfd-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="e9bfd-120">FALSE</span></span>|<span data-ttu-id="e9bfd-121">NULL</span><span class="sxs-lookup"><span data-stu-id="e9bfd-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="e9bfd-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="e9bfd-122">TRUE</span></span>|<span data-ttu-id="e9bfd-123">NULL</span><span class="sxs-lookup"><span data-stu-id="e9bfd-123">NULL</span></span>|<span data-ttu-id="e9bfd-124">NULL</span><span class="sxs-lookup"><span data-stu-id="e9bfd-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9bfd-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9bfd-125">Example</span></span>  
 <span data-ttu-id="e9bfd-126">A seguinte consulta SQL Entity usa o operador OR para combinar duas expressões de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="e9bfd-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="e9bfd-127">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e9bfd-128">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e9bfd-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e9bfd-129">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e9bfd-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e9bfd-130">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="e9bfd-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="e9bfd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9bfd-131">See Also</span></span>  
 [<span data-ttu-id="e9bfd-132">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e9bfd-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
