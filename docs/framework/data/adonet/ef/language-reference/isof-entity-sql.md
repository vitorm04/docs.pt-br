---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 097d6e7d452ee62a2c8934d2c5fcfdddbeaffc73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772366"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="e7830-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e7830-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="e7830-103">Determina se o tipo de uma expressão é do tipo especificado ou um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="e7830-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7830-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7830-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7830-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e7830-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e7830-106">Qualquer expressão de consulta válida para determinar o tipo de.</span><span class="sxs-lookup"><span data-stu-id="e7830-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="e7830-107">NOT</span><span class="sxs-lookup"><span data-stu-id="e7830-107">NOT</span></span>  
 <span data-ttu-id="e7830-108">Nega o resultado de EDM.Boolean de ESTÁ DE.</span><span class="sxs-lookup"><span data-stu-id="e7830-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="e7830-109">SOMENTE</span><span class="sxs-lookup"><span data-stu-id="e7830-109">ONLY</span></span>  
 <span data-ttu-id="e7830-110">Especifica que É returns `true` somente se `expression` é do tipo `type` e não qualquer um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="e7830-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="e7830-111">O tipo para testar `expression` contra.</span><span class="sxs-lookup"><span data-stu-id="e7830-111">The type to test `expression` against.</span></span> <span data-ttu-id="e7830-112">O tipo URL deve ser qualificada.</span><span class="sxs-lookup"><span data-stu-id="e7830-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7830-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e7830-113">Return Value</span></span>  
 <span data-ttu-id="e7830-114">`true` se `expression` é do tipo T e T é um tipo base, ou um tipo derivado de `type`; se `expression` nulo é nulo em tempo de execução; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e7830-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7830-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7830-115">Remarks</span></span>  
 <span data-ttu-id="e7830-116">As expressões `expression IS NOT OF (type)` e `expression IS NOT OF (ONLY type)` são sintaticamente equivalentes à `NOT (expression IS OF (type))` e `NOT (expression IS OF (ONLY type))`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e7830-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="e7830-117">A tabela a seguir mostra o comportamento do operador de `IS OF` sobre alguns padrões e típicos do canto.</span><span class="sxs-lookup"><span data-stu-id="e7830-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="e7830-118">Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:</span><span class="sxs-lookup"><span data-stu-id="e7830-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="e7830-119">Padrão</span><span class="sxs-lookup"><span data-stu-id="e7830-119">Pattern</span></span>|<span data-ttu-id="e7830-120">Comportamento</span><span class="sxs-lookup"><span data-stu-id="e7830-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="e7830-121">o zero ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e7830-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="e7830-122">Gera</span><span class="sxs-lookup"><span data-stu-id="e7830-122">Throws</span></span>|  
|<span data-ttu-id="e7830-123">o zero ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e7830-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="e7830-124">Gera</span><span class="sxs-lookup"><span data-stu-id="e7830-124">Throws</span></span>|  
|<span data-ttu-id="e7830-125">o zero ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="e7830-125">null IS OF (RowType)</span></span>|<span data-ttu-id="e7830-126">Gera</span><span class="sxs-lookup"><span data-stu-id="e7830-126">Throws</span></span>|  
|<span data-ttu-id="e7830-127">O DELEITE (zero) COMO EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e7830-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="e7830-128">Retorna DBNull</span><span class="sxs-lookup"><span data-stu-id="e7830-128">Returns DBNull</span></span>|  
|<span data-ttu-id="e7830-129">O DELEITE (zero) COMO ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e7830-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="e7830-130">Gera</span><span class="sxs-lookup"><span data-stu-id="e7830-130">Throws</span></span>|  
|<span data-ttu-id="e7830-131">O DELEITE (zero) COMO RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="e7830-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="e7830-132">Gera</span><span class="sxs-lookup"><span data-stu-id="e7830-132">Throws</span></span>|  
|<span data-ttu-id="e7830-133">EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e7830-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="e7830-134">Retorna retificam/falso</span><span class="sxs-lookup"><span data-stu-id="e7830-134">Returns true/false</span></span>|  
|<span data-ttu-id="e7830-135">ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e7830-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="e7830-136">Gera</span><span class="sxs-lookup"><span data-stu-id="e7830-136">Throws</span></span>|  
|<span data-ttu-id="e7830-137">RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="e7830-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="e7830-138">Gera</span><span class="sxs-lookup"><span data-stu-id="e7830-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7830-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7830-139">Example</span></span>  
 <span data-ttu-id="e7830-140">O seguinte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta usa é de operador para determinar o tipo de uma expressão de consulta e, em seguida, usa o operador de DELEITE para converter um objeto do tipo de curso em uma coleção de objetos do tipo OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="e7830-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="e7830-141">A consulta se baseia a [modelo de escola](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e7830-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="e7830-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7830-142">See also</span></span>

- [<span data-ttu-id="e7830-143">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e7830-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
