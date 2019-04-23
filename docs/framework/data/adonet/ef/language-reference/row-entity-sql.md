---
title: LINHA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: b83020601373ba93124dfb24308dd048bfa3c6dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319385"
---
# <a name="row-entity-sql"></a><span data-ttu-id="6e17a-102">LINHA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6e17a-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="6e17a-103">Constrói registros anônimos e tipados estruturalmente de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="6e17a-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e17a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e17a-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e17a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e17a-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6e17a-106">Qualquer expressão de consulta válida que retorna um valor para construir em seguida o tipo.</span><span class="sxs-lookup"><span data-stu-id="6e17a-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="6e17a-107">Especifica um alias para uma linha no tipo especificado valor.</span><span class="sxs-lookup"><span data-stu-id="6e17a-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="6e17a-108">Se um alias não for fornecido, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta gerar um alias com base no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] regras de geração de alias.</span><span class="sxs-lookup"><span data-stu-id="6e17a-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e17a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6e17a-109">Return Value</span></span>  
 <span data-ttu-id="6e17a-110">Um tipo de linha.</span><span class="sxs-lookup"><span data-stu-id="6e17a-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e17a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e17a-111">Remarks</span></span>  
 <span data-ttu-id="6e17a-112">Você usa construtores de linha no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para construir registros anônimos, tipados estrutural de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="6e17a-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="6e17a-113">O tipo do resultado de um construtor de linha é um tipo de linha cujos tipos de campo correspondem aos tipos de valores que foram usados para construir a linha.</span><span class="sxs-lookup"><span data-stu-id="6e17a-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="6e17a-114">Por exemplo, a expressão a seguir constrói um valor do tipo `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="6e17a-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="6e17a-115">Se você não fornecer um alias para um construtor de expressão em seguida, Entity Framework tentará gerar um.</span><span class="sxs-lookup"><span data-stu-id="6e17a-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="6e17a-116">Para obter mais informações, consulte a seção "Regras Serrilha" a [identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="6e17a-116">For more information, see the "Aliasing Rules" section of the [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="6e17a-117">As seguintes regras se aplicam para o construtor de serrilha de expressão em uma linha:</span><span class="sxs-lookup"><span data-stu-id="6e17a-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="6e17a-118">O construtor das expressões em uma linha não pode referenciar outras alias no mesmo construtor.</span><span class="sxs-lookup"><span data-stu-id="6e17a-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="6e17a-119">Duas expressões no mesmo construtor de linha não podem ter as mesmas alias.</span><span class="sxs-lookup"><span data-stu-id="6e17a-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="6e17a-120">Para obter mais informações sobre os construtores de consulta, consulte [construindo tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6e17a-120">For more information about query constructors, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e17a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e17a-121">Example</span></span>  
 <span data-ttu-id="6e17a-122">A seguinte consulta SQL Entity usa o operador de LINHA para construir registros anônimos, estrutural tipados.</span><span class="sxs-lookup"><span data-stu-id="6e17a-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="6e17a-123">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6e17a-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6e17a-124">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="6e17a-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6e17a-125">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6e17a-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6e17a-126">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="6e17a-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="6e17a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e17a-127">See also</span></span>

- [<span data-ttu-id="6e17a-128">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="6e17a-128">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="6e17a-129">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6e17a-129">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="6e17a-130">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="6e17a-130">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
