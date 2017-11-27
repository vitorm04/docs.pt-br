---
title: ISNULL (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31e0b77e397bd4f190119a01719da185211f7715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="90502-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="90502-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="90502-103">Determina se uma expressão de consulta é nula.</span><span class="sxs-lookup"><span data-stu-id="90502-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90502-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90502-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="90502-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="90502-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="90502-106">Qualquer expressão de consulta válida.</span><span class="sxs-lookup"><span data-stu-id="90502-106">Any valid query expression.</span></span> <span data-ttu-id="90502-107">Não pode ser uma coleção, tem membros da coleção, ou um tipo de registro com propriedades do tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="90502-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="90502-108">NOT</span><span class="sxs-lookup"><span data-stu-id="90502-108">NOT</span></span>  
 <span data-ttu-id="90502-109">Nega o resultado de EDM.Boolean É de NULO.</span><span class="sxs-lookup"><span data-stu-id="90502-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90502-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="90502-110">Return Value</span></span>  
 <span data-ttu-id="90502-111">`true` se `expression` retorna nulo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="90502-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90502-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="90502-112">Remarks</span></span>  
 <span data-ttu-id="90502-113">Use `IS NULL` para determinar se o elemento de um externo joins é nulo:</span><span class="sxs-lookup"><span data-stu-id="90502-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="90502-114">Use `IS NULL` para determinar se um membro tem um valor real:</span><span class="sxs-lookup"><span data-stu-id="90502-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="90502-115">A tabela a seguir mostra o comportamento de `IS NULL` sobre alguns padrões.</span><span class="sxs-lookup"><span data-stu-id="90502-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="90502-116">Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:</span><span class="sxs-lookup"><span data-stu-id="90502-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="90502-117">Padrão</span><span class="sxs-lookup"><span data-stu-id="90502-117">Pattern</span></span>|<span data-ttu-id="90502-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="90502-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="90502-119">o zero É NULO</span><span class="sxs-lookup"><span data-stu-id="90502-119">null IS NULL</span></span>|<span data-ttu-id="90502-120">Retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="90502-120">Returns `true`.</span></span>|  
|<span data-ttu-id="90502-121">O DELEITE zero (COMO EntityType) É NULO</span><span class="sxs-lookup"><span data-stu-id="90502-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="90502-122">Retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="90502-122">Returns `true`.</span></span>|  
|<span data-ttu-id="90502-123">O DELEITE zero (COMO ComplexType) É NULO</span><span class="sxs-lookup"><span data-stu-id="90502-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="90502-124">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="90502-124">Throws an error.</span></span>|  
|<span data-ttu-id="90502-125">O DELEITE zero (COMO RowType) É NULO</span><span class="sxs-lookup"><span data-stu-id="90502-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="90502-126">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="90502-126">Throws an error.</span></span>|  
|<span data-ttu-id="90502-127">EntityType É NULO</span><span class="sxs-lookup"><span data-stu-id="90502-127">EntityType IS NULL</span></span>|<span data-ttu-id="90502-128">Retorna `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="90502-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="90502-129">ComplexType É NULO</span><span class="sxs-lookup"><span data-stu-id="90502-129">ComplexType IS NULL</span></span>|<span data-ttu-id="90502-130">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="90502-130">Throws an error.</span></span>|  
|<span data-ttu-id="90502-131">RowType É NULO</span><span class="sxs-lookup"><span data-stu-id="90502-131">RowType IS NULL</span></span>|<span data-ttu-id="90502-132">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="90502-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="90502-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90502-133">Example</span></span>  
 <span data-ttu-id="90502-134">O seguinte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta usa o operador IS NOT NULL para determinar se uma expressão de consulta não é nulo.</span><span class="sxs-lookup"><span data-stu-id="90502-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="90502-135">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="90502-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="90502-136">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="90502-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="90502-137">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="90502-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="90502-138">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="90502-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="90502-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90502-139">See Also</span></span>  
 [<span data-ttu-id="90502-140">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="90502-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
