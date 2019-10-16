---
title: Construtor de tipo nomeado (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f40adce1a9e031ed0b7cd5d03d9c63db255aa610
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319568"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="d9d4b-102">Construtor de tipo nomeado (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d9d4b-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="d9d4b-103">Usado para criar instâncias de tipos nominais de modelo conceitual como a entidade ou tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="d9d4b-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9d4b-104">Syntax</span></span>  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d9d4b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d9d4b-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="d9d4b-106">Valor que é um identificador simples ou citado.</span><span class="sxs-lookup"><span data-stu-id="d9d4b-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="d9d4b-107">Para obter mais informações, consulte [identificadores](identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="d9d4b-107">For more information see, [Identifiers](identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="d9d4b-108">Atributos de tipo que são considerados para estar na mesma ordem que aparecem na declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="d9d4b-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9d4b-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d9d4b-109">Return Value</span></span>  
 <span data-ttu-id="d9d4b-110">Instâncias de tipos complexos nomeados e tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="d9d4b-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9d4b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9d4b-111">Remarks</span></span>  
 <span data-ttu-id="d9d4b-112">Os exemplos a seguir mostram como construir o substantivo e os tipos complexos:</span><span class="sxs-lookup"><span data-stu-id="d9d4b-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="d9d4b-113">A expressão a seguir cria uma instância de um tipo de `Person` :</span><span class="sxs-lookup"><span data-stu-id="d9d4b-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="d9d4b-114">A expressão a seguir cria uma instância de um tipo complexo:</span><span class="sxs-lookup"><span data-stu-id="d9d4b-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="d9d4b-115">A expressão a seguir cria uma instância de um tipo complexo aninhado:</span><span class="sxs-lookup"><span data-stu-id="d9d4b-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="d9d4b-116">A expressão a seguir cria uma instância de um objeto com um tipo complexo aninhado:</span><span class="sxs-lookup"><span data-stu-id="d9d4b-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="d9d4b-117">O exemplo a seguir mostra como inicializar uma propriedade de um tipo complexo para nulo:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="d9d4b-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9d4b-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9d4b-118">Example</span></span>  
 <span data-ttu-id="d9d4b-119">A seguinte consulta SQL Entity usa o construtor chamado de tipo para criar uma instância de um tipo de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="d9d4b-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="d9d4b-120">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d9d4b-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d9d4b-121">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d9d4b-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d9d4b-122">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d9d4b-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d9d4b-123">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="d9d4b-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="d9d4b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9d4b-124">See also</span></span>

- [<span data-ttu-id="d9d4b-125">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="d9d4b-125">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="d9d4b-126">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d9d4b-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
