---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: a0294f425552df3329d158d69a6d503b2f008780
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542327"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="5b381-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5b381-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="5b381-103">Determina se o tipo de uma expressão é do tipo especificado ou um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="5b381-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b381-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b381-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b381-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="5b381-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5b381-106">Qualquer expressão de consulta válida para determinar o tipo de.</span><span class="sxs-lookup"><span data-stu-id="5b381-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="5b381-107">NOT</span><span class="sxs-lookup"><span data-stu-id="5b381-107">NOT</span></span>  
 <span data-ttu-id="5b381-108">Nega o resultado de EDM.Boolean de ESTÁ DE.</span><span class="sxs-lookup"><span data-stu-id="5b381-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="5b381-109">ONLY</span><span class="sxs-lookup"><span data-stu-id="5b381-109">ONLY</span></span>  
 <span data-ttu-id="5b381-110">Especifica que É returns `true` somente se `expression` é do tipo `type` e não qualquer um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="5b381-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="5b381-111">O tipo para testar `expression` contra.</span><span class="sxs-lookup"><span data-stu-id="5b381-111">The type to test `expression` against.</span></span> <span data-ttu-id="5b381-112">O tipo URL deve ser qualificada.</span><span class="sxs-lookup"><span data-stu-id="5b381-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b381-113">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="5b381-113">Return Value</span></span>  
 <span data-ttu-id="5b381-114">`true` se `expression` é do tipo T e T é um tipo base, ou um tipo derivado de `type`; se `expression` nulo é nulo em runtime; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="5b381-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b381-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b381-115">Remarks</span></span>  
 <span data-ttu-id="5b381-116">As expressões `expression IS NOT OF (type)` e `expression IS NOT OF (ONLY type)` são sintaticamente equivalentes a `NOT (expression IS OF (type))` e `NOT (expression IS OF (ONLY type))` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5b381-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="5b381-117">A tabela a seguir mostra o comportamento do operador de `IS OF` sobre alguns padrões e típicos do canto.</span><span class="sxs-lookup"><span data-stu-id="5b381-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="5b381-118">Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:</span><span class="sxs-lookup"><span data-stu-id="5b381-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="5b381-119">Padrão</span><span class="sxs-lookup"><span data-stu-id="5b381-119">Pattern</span></span>|<span data-ttu-id="5b381-120">Comportamento</span><span class="sxs-lookup"><span data-stu-id="5b381-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="5b381-121">o zero ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5b381-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="5b381-122">Gera</span><span class="sxs-lookup"><span data-stu-id="5b381-122">Throws</span></span>|  
|<span data-ttu-id="5b381-123">o zero ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5b381-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="5b381-124">Gera</span><span class="sxs-lookup"><span data-stu-id="5b381-124">Throws</span></span>|  
|<span data-ttu-id="5b381-125">o zero ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="5b381-125">null IS OF (RowType)</span></span>|<span data-ttu-id="5b381-126">Gera</span><span class="sxs-lookup"><span data-stu-id="5b381-126">Throws</span></span>|  
|<span data-ttu-id="5b381-127">O DELEITE (zero) COMO EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5b381-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="5b381-128">Retorna DBNull</span><span class="sxs-lookup"><span data-stu-id="5b381-128">Returns DBNull</span></span>|  
|<span data-ttu-id="5b381-129">O DELEITE (zero) COMO ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5b381-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="5b381-130">Gera</span><span class="sxs-lookup"><span data-stu-id="5b381-130">Throws</span></span>|  
|<span data-ttu-id="5b381-131">O DELEITE (zero) COMO RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="5b381-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="5b381-132">Gera</span><span class="sxs-lookup"><span data-stu-id="5b381-132">Throws</span></span>|  
|<span data-ttu-id="5b381-133">EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5b381-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="5b381-134">Retorna retificam/falso</span><span class="sxs-lookup"><span data-stu-id="5b381-134">Returns true/false</span></span>|  
|<span data-ttu-id="5b381-135">ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5b381-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="5b381-136">Gera</span><span class="sxs-lookup"><span data-stu-id="5b381-136">Throws</span></span>|  
|<span data-ttu-id="5b381-137">RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="5b381-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="5b381-138">Gera</span><span class="sxs-lookup"><span data-stu-id="5b381-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b381-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b381-139">Example</span></span>  
 <span data-ttu-id="5b381-140">A consulta a seguir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador is of para determinar o tipo de uma expressão de consulta e, em seguida, usa o operador Treat para converter um objeto do tipo curso em uma coleção de objetos do tipo OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="5b381-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="5b381-141">A consulta é baseada no [modelo escolar](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5b381-141">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="5b381-142">[! Code-SQL [conceitos de entidade de DP # TREAT_ISOF] ~/Samples/Snippets/TSQL/VS_Snippets_Data/DP entityservices Concepts/TSQL/entitysql. SQL # treat_isof)]</span><span class="sxs-lookup"><span data-stu-id="5b381-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b381-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="5b381-143">See also</span></span>

- [<span data-ttu-id="5b381-144">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5b381-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
