---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: c4c4cbf74cb17cf43e79c42ff42d1e68122fd534
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319716"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="e8645-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e8645-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="e8645-103">Determina se o tipo de uma expressão é do tipo especificado ou um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="e8645-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8645-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8645-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8645-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e8645-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e8645-106">Qualquer expressão de consulta válida para determinar o tipo de.</span><span class="sxs-lookup"><span data-stu-id="e8645-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="e8645-107">NOT</span><span class="sxs-lookup"><span data-stu-id="e8645-107">NOT</span></span>  
 <span data-ttu-id="e8645-108">Nega o resultado de EDM.Boolean de ESTÁ DE.</span><span class="sxs-lookup"><span data-stu-id="e8645-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="e8645-109">SOMENTE</span><span class="sxs-lookup"><span data-stu-id="e8645-109">ONLY</span></span>  
 <span data-ttu-id="e8645-110">Especifica que É returns `true` somente se `expression` é do tipo `type` e não qualquer um de seus subtipos.</span><span class="sxs-lookup"><span data-stu-id="e8645-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="e8645-111">O tipo para testar `expression` contra.</span><span class="sxs-lookup"><span data-stu-id="e8645-111">The type to test `expression` against.</span></span> <span data-ttu-id="e8645-112">O tipo URL deve ser qualificada.</span><span class="sxs-lookup"><span data-stu-id="e8645-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8645-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e8645-113">Return Value</span></span>  
 <span data-ttu-id="e8645-114">`true` se `expression` é do tipo T e T é um tipo base, ou um tipo derivado de `type`; se `expression` nulo é nulo em tempo de execução; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e8645-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8645-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8645-115">Remarks</span></span>  
 <span data-ttu-id="e8645-116">As expressões `expression IS NOT OF (type)` e `expression IS NOT OF (ONLY type)` são sintaticamente equivalentes a `NOT (expression IS OF (type))` e `NOT (expression IS OF (ONLY type))`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e8645-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="e8645-117">A tabela a seguir mostra o comportamento do operador de `IS OF` sobre alguns padrões e típicos do canto.</span><span class="sxs-lookup"><span data-stu-id="e8645-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="e8645-118">Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:</span><span class="sxs-lookup"><span data-stu-id="e8645-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="e8645-119">Padrão</span><span class="sxs-lookup"><span data-stu-id="e8645-119">Pattern</span></span>|<span data-ttu-id="e8645-120">Comportamento</span><span class="sxs-lookup"><span data-stu-id="e8645-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="e8645-121">o zero ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e8645-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="e8645-122">Gera</span><span class="sxs-lookup"><span data-stu-id="e8645-122">Throws</span></span>|  
|<span data-ttu-id="e8645-123">o zero ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e8645-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="e8645-124">Gera</span><span class="sxs-lookup"><span data-stu-id="e8645-124">Throws</span></span>|  
|<span data-ttu-id="e8645-125">o zero ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="e8645-125">null IS OF (RowType)</span></span>|<span data-ttu-id="e8645-126">Gera</span><span class="sxs-lookup"><span data-stu-id="e8645-126">Throws</span></span>|  
|<span data-ttu-id="e8645-127">O DELEITE (zero) COMO EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e8645-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="e8645-128">Retorna DBNull</span><span class="sxs-lookup"><span data-stu-id="e8645-128">Returns DBNull</span></span>|  
|<span data-ttu-id="e8645-129">O DELEITE (zero) COMO ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e8645-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="e8645-130">Gera</span><span class="sxs-lookup"><span data-stu-id="e8645-130">Throws</span></span>|  
|<span data-ttu-id="e8645-131">O DELEITE (zero) COMO RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="e8645-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="e8645-132">Gera</span><span class="sxs-lookup"><span data-stu-id="e8645-132">Throws</span></span>|  
|<span data-ttu-id="e8645-133">EntityType ESTÁ DE (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e8645-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="e8645-134">Retorna retificam/falso</span><span class="sxs-lookup"><span data-stu-id="e8645-134">Returns true/false</span></span>|  
|<span data-ttu-id="e8645-135">ComplexType ESTÁ DE (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e8645-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="e8645-136">Gera</span><span class="sxs-lookup"><span data-stu-id="e8645-136">Throws</span></span>|  
|<span data-ttu-id="e8645-137">RowType ESTÁ DE (RowType)</span><span class="sxs-lookup"><span data-stu-id="e8645-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="e8645-138">Gera</span><span class="sxs-lookup"><span data-stu-id="e8645-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e8645-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8645-139">Example</span></span>  
 <span data-ttu-id="e8645-140">A consulta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir usa o operador IS OF para determinar o tipo de uma expressão de consulta e, em seguida, usa o operador TREAT para converter um objeto do curso de tipo em uma coleção de objetos do tipo OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="e8645-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="e8645-141">A consulta é baseada no [modelo escolar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e8645-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="e8645-142">[! Code-SQL [conceitos de entidade de DP # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices Concepts/TSQL/entitysql. SQL # TREAT_ISOF)]</span><span class="sxs-lookup"><span data-stu-id="e8645-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8645-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8645-143">See also</span></span>

- [<span data-ttu-id="e8645-144">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e8645-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
