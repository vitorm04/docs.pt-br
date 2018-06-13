---
title: CRIARREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 44954dcc1f3407a768ba23fe87ac4b4abcf1bac5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761331"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="02988-102">CRIARREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="02988-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="02988-103">Fabrica referências a uma entidade em um entityset.</span><span class="sxs-lookup"><span data-stu-id="02988-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02988-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02988-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="02988-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="02988-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="02988-106">O identificador de entityset, não um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="02988-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="02988-107">Uma expressão linha tipada que corresponde a propriedades chave do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="02988-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02988-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="02988-108">Remarks</span></span>  
 <span data-ttu-id="02988-109">`row_typed_expression` deve ser estrutural equivalente ao tipo principal para a entidade.</span><span class="sxs-lookup"><span data-stu-id="02988-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="02988-110">Isto é, deve ter o mesmo número e tipos de campos na mesma ordem como as chaves de entidade.</span><span class="sxs-lookup"><span data-stu-id="02988-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="02988-111">No exemplo abaixo, os pedidos e BadOrders são ambos os entitysets ordem de tipo, e é a identificação assumida para ser a única propriedade de chave pedido.</span><span class="sxs-lookup"><span data-stu-id="02988-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="02988-112">O exemplo ilustra como nós podemos gerar uma referência a uma entidade em BadOrders.</span><span class="sxs-lookup"><span data-stu-id="02988-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="02988-113">Observe que a referência pode oscilar.</span><span class="sxs-lookup"><span data-stu-id="02988-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="02988-114">Isto é, a referência não pode realmente identificar uma entidade específica.</span><span class="sxs-lookup"><span data-stu-id="02988-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="02988-115">Nesses casos, uma operação de `DEREF` na referência retorna um zero.</span><span class="sxs-lookup"><span data-stu-id="02988-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="02988-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02988-116">Example</span></span>  
 <span data-ttu-id="02988-117">A seguinte consulta SQL Entity usa o operador de CREATEREF para fabricar referências a uma entidade em um conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="02988-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="02988-118">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="02988-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="02988-119">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="02988-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="02988-120">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="02988-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="02988-121">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="02988-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="02988-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02988-122">See Also</span></span>  
 [<span data-ttu-id="02988-123">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="02988-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="02988-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="02988-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="02988-125">KEY</span><span class="sxs-lookup"><span data-stu-id="02988-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="02988-126">REF</span><span class="sxs-lookup"><span data-stu-id="02988-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
