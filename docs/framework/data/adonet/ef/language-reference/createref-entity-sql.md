---
title: CRIARREF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9fe960d5b19f5119f2337ec410738a2df31f20c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="createref-entity-sql"></a><span data-ttu-id="89863-102">CRIARREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="89863-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="89863-103">Fabrica referências a uma entidade em um entityset.</span><span class="sxs-lookup"><span data-stu-id="89863-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89863-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89863-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="89863-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="89863-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="89863-106">O identificador de entityset, não um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="89863-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="89863-107">Uma expressão linha tipada que corresponde a propriedades chave do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="89863-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89863-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="89863-108">Remarks</span></span>  
 <span data-ttu-id="89863-109">`row_typed_expression` deve ser estrutural equivalente ao tipo principal para a entidade.</span><span class="sxs-lookup"><span data-stu-id="89863-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="89863-110">Isto é, deve ter o mesmo número e tipos de campos na mesma ordem como as chaves de entidade.</span><span class="sxs-lookup"><span data-stu-id="89863-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="89863-111">No exemplo abaixo, os pedidos e BadOrders são ambos os entitysets ordem de tipo, e é a identificação assumida para ser a única propriedade de chave pedido.</span><span class="sxs-lookup"><span data-stu-id="89863-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="89863-112">O exemplo ilustra como nós podemos gerar uma referência a uma entidade em BadOrders.</span><span class="sxs-lookup"><span data-stu-id="89863-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="89863-113">Observe que a referência pode oscilar.</span><span class="sxs-lookup"><span data-stu-id="89863-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="89863-114">Isto é, a referência não pode realmente identificar uma entidade específica.</span><span class="sxs-lookup"><span data-stu-id="89863-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="89863-115">Nesses casos, uma operação de `DEREF` na referência retorna um zero.</span><span class="sxs-lookup"><span data-stu-id="89863-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="89863-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89863-116">Example</span></span>  
 <span data-ttu-id="89863-117">A seguinte consulta SQL Entity usa o operador de CREATEREF para fabricar referências a uma entidade em um conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="89863-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="89863-118">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="89863-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="89863-119">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="89863-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="89863-120">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="89863-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="89863-121">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="89863-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="89863-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89863-122">See Also</span></span>  
 [<span data-ttu-id="89863-123">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="89863-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="89863-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="89863-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="89863-125">CHAVE</span><span class="sxs-lookup"><span data-stu-id="89863-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="89863-126">REF</span><span class="sxs-lookup"><span data-stu-id="89863-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
