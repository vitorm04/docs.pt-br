---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 894d3ab91623aa4246bf7735fb1b7d04e066825a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072630"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="635bb-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="635bb-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="635bb-103">Determina se uma expressão de consulta é nula.</span><span class="sxs-lookup"><span data-stu-id="635bb-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="635bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="635bb-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="635bb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="635bb-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="635bb-106">Qualquer expressão de consulta válida.</span><span class="sxs-lookup"><span data-stu-id="635bb-106">Any valid query expression.</span></span> <span data-ttu-id="635bb-107">Não pode ser uma coleção, tem membros da coleção, ou um tipo de registro com propriedades do tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="635bb-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="635bb-108">NOT</span><span class="sxs-lookup"><span data-stu-id="635bb-108">NOT</span></span>  
 <span data-ttu-id="635bb-109">Nega o resultado de EDM.Boolean É de NULO.</span><span class="sxs-lookup"><span data-stu-id="635bb-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="635bb-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="635bb-110">Return Value</span></span>  
 `true` <span data-ttu-id="635bb-111">Se `expression` retorna nulo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="635bb-111">if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="635bb-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="635bb-112">Remarks</span></span>  
 <span data-ttu-id="635bb-113">Use `IS NULL` para determinar se o elemento de um externo joins é nulo:</span><span class="sxs-lookup"><span data-stu-id="635bb-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="635bb-114">Use `IS NULL` para determinar se um membro tem um valor real:</span><span class="sxs-lookup"><span data-stu-id="635bb-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="635bb-115">A tabela a seguir mostra o comportamento de `IS NULL` sobre alguns padrões.</span><span class="sxs-lookup"><span data-stu-id="635bb-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="635bb-116">Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:</span><span class="sxs-lookup"><span data-stu-id="635bb-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="635bb-117">Padrão</span><span class="sxs-lookup"><span data-stu-id="635bb-117">Pattern</span></span>|<span data-ttu-id="635bb-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="635bb-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="635bb-119">o zero É NULO</span><span class="sxs-lookup"><span data-stu-id="635bb-119">null IS NULL</span></span>|<span data-ttu-id="635bb-120">Retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="635bb-120">Returns `true`.</span></span>|  
|<span data-ttu-id="635bb-121">O DELEITE zero (COMO EntityType) É NULO</span><span class="sxs-lookup"><span data-stu-id="635bb-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="635bb-122">Retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="635bb-122">Returns `true`.</span></span>|  
|<span data-ttu-id="635bb-123">O DELEITE zero (COMO ComplexType) É NULO</span><span class="sxs-lookup"><span data-stu-id="635bb-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="635bb-124">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="635bb-124">Throws an error.</span></span>|  
|<span data-ttu-id="635bb-125">O DELEITE zero (COMO RowType) É NULO</span><span class="sxs-lookup"><span data-stu-id="635bb-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="635bb-126">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="635bb-126">Throws an error.</span></span>|  
|<span data-ttu-id="635bb-127">EntityType É NULO</span><span class="sxs-lookup"><span data-stu-id="635bb-127">EntityType IS NULL</span></span>|<span data-ttu-id="635bb-128">Retorna `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="635bb-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="635bb-129">ComplexType É NULO</span><span class="sxs-lookup"><span data-stu-id="635bb-129">ComplexType IS NULL</span></span>|<span data-ttu-id="635bb-130">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="635bb-130">Throws an error.</span></span>|  
|<span data-ttu-id="635bb-131">RowType É NULO</span><span class="sxs-lookup"><span data-stu-id="635bb-131">RowType IS NULL</span></span>|<span data-ttu-id="635bb-132">Gerencie um erro.</span><span class="sxs-lookup"><span data-stu-id="635bb-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="635bb-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="635bb-133">Example</span></span>  
 <span data-ttu-id="635bb-134">O seguinte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta usa o operador IS NOT NULL para determinar se uma expressão de consulta não é nula.</span><span class="sxs-lookup"><span data-stu-id="635bb-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="635bb-135">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="635bb-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="635bb-136">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="635bb-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="635bb-137">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="635bb-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="635bb-138">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="635bb-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="635bb-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="635bb-139">See also</span></span>

- [<span data-ttu-id="635bb-140">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="635bb-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
