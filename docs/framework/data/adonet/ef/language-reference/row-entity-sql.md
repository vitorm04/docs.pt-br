---
title: LINHA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 4fb16fe0072066580bff36ac0879ff38217f1e34
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319384"
---
# <a name="row-entity-sql"></a><span data-ttu-id="2a2f3-102">LINHA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2a2f3-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="2a2f3-103">Constrói registros anônimos e tipados estruturalmente de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a2f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a2f3-104">Syntax</span></span>  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2a2f3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2a2f3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2a2f3-106">Qualquer expressão de consulta válida que retorna um valor para construir em seguida o tipo.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="2a2f3-107">Especifica um alias para uma linha no tipo especificado valor.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="2a2f3-108">Se um alias não for fornecido, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tentará gerar um alias com base nas regras de geração de alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a2f3-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a2f3-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2a2f3-109">Return Value</span></span>  
 <span data-ttu-id="2a2f3-110">Um tipo de linha.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a2f3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a2f3-111">Remarks</span></span>  
 <span data-ttu-id="2a2f3-112">Você usa construtores de linha no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para construir registros anônimos e tipados de forma estrutural a partir de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="2a2f3-113">O tipo do resultado de um construtor de linha é um tipo de linha cujos tipos de campo correspondem aos tipos de valores que foram usados para construir a linha.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="2a2f3-114">Por exemplo, a expressão a seguir constrói um valor do tipo `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="2a2f3-115">Se você não fornecer um alias para um construtor de expressão em seguida, Entity Framework tentará gerar um.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="2a2f3-116">Para obter mais informações, consulte a seção "regras de alias" do tópico [identificadores](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="2a2f3-116">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="2a2f3-117">As seguintes regras se aplicam para o construtor de serrilha de expressão em uma linha:</span><span class="sxs-lookup"><span data-stu-id="2a2f3-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="2a2f3-118">O construtor das expressões em uma linha não pode referenciar outras alias no mesmo construtor.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="2a2f3-119">Duas expressões no mesmo construtor de linha não podem ter as mesmas alias.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="2a2f3-120">Para obter mais informações sobre construtores de consulta, consulte [construindo tipos](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2a2f3-120">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a2f3-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a2f3-121">Example</span></span>  
 <span data-ttu-id="2a2f3-122">A seguinte consulta SQL Entity usa o operador de LINHA para construir registros anônimos, estrutural tipados.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="2a2f3-123">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2a2f3-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2a2f3-124">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2a2f3-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2a2f3-125">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2a2f3-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2a2f3-126">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="2a2f3-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a><span data-ttu-id="2a2f3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a2f3-127">See also</span></span>

- [<span data-ttu-id="2a2f3-128">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="2a2f3-128">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="2a2f3-129">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2a2f3-129">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2a2f3-130">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="2a2f3-130">Type Definitions</span></span>](type-definitions-entity-sql.md)
