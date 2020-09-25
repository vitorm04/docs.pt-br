---
title: LINHA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 2ab91d0c6d3c3ed3f88a7f0ddbf3a6c2f36d8b04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202247"
---
# <a name="row-entity-sql"></a><span data-ttu-id="2b446-102">LINHA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b446-102">ROW (Entity SQL)</span></span>

<span data-ttu-id="2b446-103">Constrói registros anônimos e tipados estruturalmente de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="2b446-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b446-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b446-104">Syntax</span></span>  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b446-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2b446-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="2b446-106">Qualquer expressão de consulta válida que retorna um valor para construir em seguida o tipo.</span><span class="sxs-lookup"><span data-stu-id="2b446-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="2b446-107">Especifica um alias para uma linha no tipo especificado valor.</span><span class="sxs-lookup"><span data-stu-id="2b446-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="2b446-108">Se um alias não for fornecido, o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tentará gerar um alias com base nas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] regras de geração de alias.</span><span class="sxs-lookup"><span data-stu-id="2b446-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b446-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2b446-109">Return Value</span></span>  

 <span data-ttu-id="2b446-110">Um tipo de linha.</span><span class="sxs-lookup"><span data-stu-id="2b446-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b446-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b446-111">Remarks</span></span>  

 <span data-ttu-id="2b446-112">Você usa construtores de linha no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para construir registros anônimos e tipados de forma estrutural a partir de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="2b446-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="2b446-113">O tipo do resultado de um construtor de linha é um tipo de linha cujos tipos de campo correspondem aos tipos de valores que foram usados para construir a linha.</span><span class="sxs-lookup"><span data-stu-id="2b446-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="2b446-114">Por exemplo, a expressão a seguir constrói um valor do tipo `Record(a int, b string, c int)` .</span><span class="sxs-lookup"><span data-stu-id="2b446-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="2b446-115">Se você não fornecer um alias para um construtor de expressão em seguida, Entity Framework tentará gerar um.</span><span class="sxs-lookup"><span data-stu-id="2b446-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="2b446-116">Para obter mais informações, consulte a seção "regras de alias" do tópico [identificadores](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="2b446-116">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="2b446-117">As seguintes regras se aplicam para o construtor de serrilha de expressão em uma linha:</span><span class="sxs-lookup"><span data-stu-id="2b446-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="2b446-118">O construtor das expressões em uma linha não pode referenciar outras alias no mesmo construtor.</span><span class="sxs-lookup"><span data-stu-id="2b446-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="2b446-119">Duas expressões no mesmo construtor de linha não podem ter as mesmas alias.</span><span class="sxs-lookup"><span data-stu-id="2b446-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="2b446-120">Para obter mais informações sobre construtores de consulta, consulte [construindo tipos](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2b446-120">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b446-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b446-121">Example</span></span>  

 <span data-ttu-id="2b446-122">A seguinte consulta SQL Entity usa o operador de LINHA para construir registros anônimos, estrutural tipados.</span><span class="sxs-lookup"><span data-stu-id="2b446-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="2b446-123">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2b446-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b446-124">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2b446-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2b446-125">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2b446-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2b446-126">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="2b446-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a><span data-ttu-id="2b446-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="2b446-127">See also</span></span>

- [<span data-ttu-id="2b446-128">Construir tipos</span><span class="sxs-lookup"><span data-stu-id="2b446-128">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="2b446-129">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2b446-129">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2b446-130">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="2b446-130">Type Definitions</span></span>](type-definitions-entity-sql.md)
