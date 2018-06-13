---
title: TRATAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 932f335bf6a502b031dcf09b8050e278a0bbe9f8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763970"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="babf0-102">TRATAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="babf0-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="babf0-103">Trata um objeto de um tipo base específico como um objeto do tipo derivado especificado.</span><span class="sxs-lookup"><span data-stu-id="babf0-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babf0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="babf0-104">Syntax</span></span>  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="babf0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="babf0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="babf0-106">Qualquer expressão de consulta válida que retorna uma entidade.</span><span class="sxs-lookup"><span data-stu-id="babf0-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babf0-107">O tipo da expressão especificada deve ser um subtipo do tipo de dados especificado, ou o tipo de dados deve ser um subtipo do tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="babf0-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="babf0-108">Um tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="babf0-108">An entity type.</span></span> <span data-ttu-id="babf0-109">O tipo deve ser qualificado por um namespace.</span><span class="sxs-lookup"><span data-stu-id="babf0-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babf0-110">A expressão especificada deve ser um subtipo do tipo de dados especificado, ou o tipo de dados deve ser um subtipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="babf0-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="babf0-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="babf0-111">Return Value</span></span>  
 <span data-ttu-id="babf0-112">Um valor de tipo de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="babf0-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="babf0-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="babf0-113">Remarks</span></span>  
 <span data-ttu-id="babf0-114">O DELEITE é usado para executar upcasting entre classes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="babf0-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="babf0-115">Por exemplo, se `Employee` deriva de `Person` e p é do tipo `Person`, upcasts de `TREAT(p AS NamespaceName.Employee)` uma instância genérica de `Person` a `Employee`; isto é, permite que você trate p como `Employee`.</span><span class="sxs-lookup"><span data-stu-id="babf0-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="babf0-116">O DELEITE é usado em cenários de herança onde você pode fazer uma consulta como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="babf0-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="babf0-117">As entidades de `Person` de upcasts desta consulta a `Employee` tipo.</span><span class="sxs-lookup"><span data-stu-id="babf0-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="babf0-118">Se o valor de p verdade não é do tipo `Employee`, a expressão produz o valor `null`.</span><span class="sxs-lookup"><span data-stu-id="babf0-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babf0-119">A expressão especificada `Employee` deve ser um subtipo do tipo de dados especificado `Person`, ou o tipo de dados deve ser um subtipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="babf0-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="babf0-120">Caso contrário, a expressão resultará em um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="babf0-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="babf0-121">A tabela a seguir mostra o comportamento de tratam sobre alguns padrões típicos e alguns padrões menos comuns.</span><span class="sxs-lookup"><span data-stu-id="babf0-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="babf0-122">Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:</span><span class="sxs-lookup"><span data-stu-id="babf0-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="babf0-123">Padrão</span><span class="sxs-lookup"><span data-stu-id="babf0-123">Pattern</span></span>|<span data-ttu-id="babf0-124">Comportamento</span><span class="sxs-lookup"><span data-stu-id="babf0-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="babf0-125">Retorna `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="babf0-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="babf0-126">Gerencie uma exceção.</span><span class="sxs-lookup"><span data-stu-id="babf0-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="babf0-127">Gerencie uma exceção</span><span class="sxs-lookup"><span data-stu-id="babf0-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="babf0-128">Retorna `EntityType` ou `null`.</span><span class="sxs-lookup"><span data-stu-id="babf0-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="babf0-129">Gerencie uma exceção.</span><span class="sxs-lookup"><span data-stu-id="babf0-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="babf0-130">Gerencie uma exceção.</span><span class="sxs-lookup"><span data-stu-id="babf0-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="babf0-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="babf0-131">Example</span></span>  
 <span data-ttu-id="babf0-132">A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de DELEITE para converter um objeto do traço de tipo a uma coleção de objetos do tipo OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="babf0-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="babf0-133">A consulta se baseia o [modelo School](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="babf0-133">The query is based on the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="babf0-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="babf0-134">See Also</span></span>  
 [<span data-ttu-id="babf0-135">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="babf0-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="babf0-136">Tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="babf0-136">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
