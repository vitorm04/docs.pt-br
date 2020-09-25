---
title: CRIARREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c2a57116f56abf4db3caabcfe3acd0d8afbcf4eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201051"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="135a2-102">CRIARREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="135a2-102">CREATEREF (Entity SQL)</span></span>

<span data-ttu-id="135a2-103">Fabrica referências a uma entidade em um entityset.</span><span class="sxs-lookup"><span data-stu-id="135a2-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="135a2-104">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="135a2-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="135a2-105">Arguments</span></span>  

 `entityset_identifier`  
 <span data-ttu-id="135a2-106">O identificador de entityset, não um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="135a2-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="135a2-107">Uma expressão linha tipada que corresponde a propriedades chave do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="135a2-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="135a2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="135a2-108">Remarks</span></span>  

 <span data-ttu-id="135a2-109">`row_typed_expression` deve ser estrutural equivalente ao tipo principal para a entidade.</span><span class="sxs-lookup"><span data-stu-id="135a2-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="135a2-110">Isto é, deve ter o mesmo número e tipos de campos na mesma ordem como as chaves de entidade.</span><span class="sxs-lookup"><span data-stu-id="135a2-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="135a2-111">No exemplo abaixo, os pedidos e BadOrders são ambos os entitysets ordem de tipo, e é a identificação assumida para ser a única propriedade de chave pedido.</span><span class="sxs-lookup"><span data-stu-id="135a2-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="135a2-112">O exemplo ilustra como nós podemos gerar uma referência a uma entidade em BadOrders.</span><span class="sxs-lookup"><span data-stu-id="135a2-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="135a2-113">Observe que a referência pode oscilar.</span><span class="sxs-lookup"><span data-stu-id="135a2-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="135a2-114">Isto é, a referência não pode realmente identificar uma entidade específica.</span><span class="sxs-lookup"><span data-stu-id="135a2-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="135a2-115">Nesses casos, uma operação de `DEREF` na referência retorna um zero.</span><span class="sxs-lookup"><span data-stu-id="135a2-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="135a2-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="135a2-116">Example</span></span>  

 <span data-ttu-id="135a2-117">A seguinte consulta SQL Entity usa o operador de CREATEREF para fabricar referências a uma entidade em um conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="135a2-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="135a2-118">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="135a2-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="135a2-119">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="135a2-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="135a2-120">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="135a2-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="135a2-121">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="135a2-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="135a2-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="135a2-122">See also</span></span>

- [<span data-ttu-id="135a2-123">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="135a2-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="135a2-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="135a2-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="135a2-125">KEY</span><span class="sxs-lookup"><span data-stu-id="135a2-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="135a2-126">REFERÊNCIA</span><span class="sxs-lookup"><span data-stu-id="135a2-126">REF</span></span>](ref-entity-sql.md)
