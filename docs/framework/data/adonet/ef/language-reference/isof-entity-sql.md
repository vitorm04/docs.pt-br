---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 7aecb8e2740ffd711278bfd5735c71c2dacf9c3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="isof-entity-sql"></a><span data-ttu-id="88cd9-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="88cd9-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="88cd9-103">Determina se o tipo de uma expressão é do tipo especificado ou um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="88cd9-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cd9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88cd9-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="88cd9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="88cd9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="88cd9-106">Qualquer expressão de consulta válida para determinar o tipo de.</span><span class="sxs-lookup"><span data-stu-id="88cd9-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="88cd9-107">NOT</span><span class="sxs-lookup"><span data-stu-id="88cd9-107">NOT</span></span>  
 <span data-ttu-id="88cd9-108">Nega o resultado de EDM.Boolean de ESTÁ DE.</span><span class="sxs-lookup"><span data-stu-id="88cd9-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="88cd9-109">SOMENTE</span><span class="sxs-lookup"><span data-stu-id="88cd9-109">ONLY</span></span>  
 <span data-ttu-id="88cd9-110">Especifica que É returns `true` somente se `expression` é do tipo `type` e não qualquer um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="88cd9-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="88cd9-111">O tipo para testar `expression` contra.</span><span class="sxs-lookup"><span data-stu-id="88cd9-111">The type to test `expression` against.</span></span> <span data-ttu-id="88cd9-112">O tipo URL deve ser qualificada.</span><span class="sxs-lookup"><span data-stu-id="88cd9-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88cd9-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="88cd9-113">Return Value</span></span>  
 <span data-ttu-id="88cd9-114">`true` se `expression` é do tipo T e T é um tipo base, ou um tipo derivado de `type`; se `expression` nulo é nulo em tempo de execução; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="88cd9-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88cd9-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="88cd9-115">Remarks</span></span>  
 <span data-ttu-id="88cd9-116">As expressões `expression IS NOT OF (type)` e `expression IS NOT OF (ONLY type)` são sintaticamente equivalentes à `NOT (expression IS OF (type))` e `NOT (expression IS OF (ONLY type))`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="88cd9-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="88cd9-117">A tabela a seguir mostra o comportamento do operador de `IS OF` sobre alguns padrões e típicos do canto.</span><span class="sxs-lookup"><span data-stu-id="88cd9-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="88cd9-118">Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:</span><span class="sxs-lookup"><span data-stu-id="88cd9-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="88cd9-119">Padrão</span><span class="sxs-lookup"><span data-stu-id="88cd9-119">Pattern</span></span>|<span data-ttu-id="88cd9-120">Comportamento</span><span class="sxs-lookup"><span data-stu-id="88cd9-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="88cd9-121">o zero ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="88cd9-122">Gera</span><span class="sxs-lookup"><span data-stu-id="88cd9-122">Throws</span></span>|  
|<span data-ttu-id="88cd9-123">o zero ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="88cd9-124">Gera</span><span class="sxs-lookup"><span data-stu-id="88cd9-124">Throws</span></span>|  
|<span data-ttu-id="88cd9-125">o zero ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-125">null IS OF (RowType)</span></span>|<span data-ttu-id="88cd9-126">Gera</span><span class="sxs-lookup"><span data-stu-id="88cd9-126">Throws</span></span>|  
|<span data-ttu-id="88cd9-127">O DELEITE (zero) COMO EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="88cd9-128">Retorna DBNull</span><span class="sxs-lookup"><span data-stu-id="88cd9-128">Returns DBNull</span></span>|  
|<span data-ttu-id="88cd9-129">O DELEITE (zero) COMO ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="88cd9-130">Gera</span><span class="sxs-lookup"><span data-stu-id="88cd9-130">Throws</span></span>|  
|<span data-ttu-id="88cd9-131">O DELEITE (zero) COMO RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="88cd9-132">Gera</span><span class="sxs-lookup"><span data-stu-id="88cd9-132">Throws</span></span>|  
|<span data-ttu-id="88cd9-133">EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="88cd9-134">Retorna retificam/falso</span><span class="sxs-lookup"><span data-stu-id="88cd9-134">Returns true/false</span></span>|  
|<span data-ttu-id="88cd9-135">ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="88cd9-136">Gera</span><span class="sxs-lookup"><span data-stu-id="88cd9-136">Throws</span></span>|  
|<span data-ttu-id="88cd9-137">RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="88cd9-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="88cd9-138">Gera</span><span class="sxs-lookup"><span data-stu-id="88cd9-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="88cd9-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88cd9-139">Example</span></span>  
 <span data-ttu-id="88cd9-140">O seguinte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta usa o operador é de para determinar o tipo de uma expressão de consulta e, em seguida, usa o operador de tratar para converter um objeto do tipo de curso em uma coleção de objetos do tipo OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="88cd9-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="88cd9-141">A consulta se baseia o [modelo School](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="88cd9-141">The query is based on the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="88cd9-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88cd9-142">See Also</span></span>  
 [<span data-ttu-id="88cd9-143">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="88cd9-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
