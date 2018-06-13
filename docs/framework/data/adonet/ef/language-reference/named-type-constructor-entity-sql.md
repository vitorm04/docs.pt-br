---
title: Construtor de tipo nomeado (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 9ffaf55ed54e8479a56e6f9fc4d7a5efe47f8e2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763157"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="70c65-102">Construtor de tipo nomeado (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="70c65-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="70c65-103">Usado para criar instâncias de tipos nominais de modelo conceitual como a entidade ou tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="70c65-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c65-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70c65-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="70c65-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="70c65-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="70c65-106">Valor que é um identificador simples ou citado.</span><span class="sxs-lookup"><span data-stu-id="70c65-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="70c65-107">Para obter mais informações, consulte [identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="70c65-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="70c65-108">Atributos de tipo que são considerados para estar na mesma ordem que aparecem na declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="70c65-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70c65-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="70c65-109">Return Value</span></span>  
 <span data-ttu-id="70c65-110">Instâncias de tipos complexos nomeados e tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="70c65-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70c65-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="70c65-111">Remarks</span></span>  
 <span data-ttu-id="70c65-112">Os exemplos a seguir mostram como construir o substantivo e os tipos complexos:</span><span class="sxs-lookup"><span data-stu-id="70c65-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="70c65-113">A expressão a seguir cria uma instância de um tipo de `Person` :</span><span class="sxs-lookup"><span data-stu-id="70c65-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="70c65-114">A expressão a seguir cria uma instância de um tipo complexo:</span><span class="sxs-lookup"><span data-stu-id="70c65-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="70c65-115">A expressão a seguir cria uma instância de um tipo complexo aninhado:</span><span class="sxs-lookup"><span data-stu-id="70c65-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="70c65-116">A expressão a seguir cria uma instância de um objeto com um tipo complexo aninhado:</span><span class="sxs-lookup"><span data-stu-id="70c65-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="70c65-117">O exemplo a seguir mostra como inicializar uma propriedade de um tipo complexo para nulo:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="70c65-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="70c65-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70c65-118">Example</span></span>  
 <span data-ttu-id="70c65-119">A seguinte consulta SQL Entity usa o construtor chamado de tipo para criar uma instância de um tipo de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="70c65-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="70c65-120">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="70c65-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="70c65-121">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="70c65-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="70c65-122">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="70c65-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="70c65-123">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="70c65-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="70c65-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70c65-124">See Also</span></span>  
 [<span data-ttu-id="70c65-125">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="70c65-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="70c65-126">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="70c65-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
