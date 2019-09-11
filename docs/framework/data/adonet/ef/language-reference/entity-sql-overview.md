---
title: Visão geral da Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 8f40a34f361669d2b8d89b63b3187cae6bf705d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854487"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="fefb0-102">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fefb0-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="fefb0-103">é uma linguagem semelhante a SQL que permite consultar modelos conceituais na Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fefb0-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="fefb0-104">Os modelos conceituais representam dados como entidades e relações [!INCLUDE[esql](../../../../../../includes/esql-md.md)] e permitem que você consulte essas entidades e relações em um formato familiar para aqueles que usaram o SQL.</span><span class="sxs-lookup"><span data-stu-id="fefb0-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
      
 <span data-ttu-id="fefb0-105">O Entity Framework funciona com provedores de dados específicos de armazenamento para converter [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Generic em consultas específicas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="fefb0-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="fefb0-106">O provedor EntityClient permite executar um comando [!INCLUDE[esql](../../../../../../includes/esql-md.md)] em um modelo de entidade e retornar tipos de dados ricos que incluem resultados escalares, conjuntos de resultados e gráficos de objeto.</span><span class="sxs-lookup"><span data-stu-id="fefb0-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="fefb0-107">Ao criar objetos <xref:System.Data.EntityClient.EntityCommand>, você pode especificar um nome de procedimento armazenado ou o texto de uma consulta atribuindo uma cadeia de caracteres de consulta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a sua propriedade <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fefb0-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="fefb0-108">O <xref:System.Data.EntityClient.EntityDataReader> expõe os resultados da execução de um <xref:System.Data.EntityClient.EntityCommand> em um EDM.</span><span class="sxs-lookup"><span data-stu-id="fefb0-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="fefb0-109">Para executar o comando que retorna <xref:System.Data.EntityClient.EntityDataReader>, chame <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="fefb0-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="fefb0-110">Além do provedor EntityClient, o Entity Framework permite que você use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o para executar consultas em um modelo conceitual e retornar dados como objetos CLR fortemente tipados que são instâncias de tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="fefb0-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="fefb0-111">Para obter mais informações, consulte [trabalhando com objetos](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="fefb0-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="fefb0-112">Esta seção fornece informações conceituais sobre a linguagem [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fefb0-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fefb0-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fefb0-113">In This Section</span></span>  
 [<span data-ttu-id="fefb0-114">Diferenças entre o Entity SQL e o Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fefb0-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="fefb0-115">Referência rápida de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fefb0-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="fefb0-116">Sistema de tipos</span><span class="sxs-lookup"><span data-stu-id="fefb0-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-117">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="fefb0-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-118">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="fefb0-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-119">Cache de plano de consulta</span><span class="sxs-lookup"><span data-stu-id="fefb0-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-120">Namespaces</span><span class="sxs-lookup"><span data-stu-id="fefb0-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-121">Identificadores</span><span class="sxs-lookup"><span data-stu-id="fefb0-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-122">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fefb0-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-123">Variáveis</span><span class="sxs-lookup"><span data-stu-id="fefb0-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-124">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="fefb0-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-125">Literais</span><span class="sxs-lookup"><span data-stu-id="fefb0-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-126">Literais nulos e inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="fefb0-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-127">Conjunto de caracteres de entrada</span><span class="sxs-lookup"><span data-stu-id="fefb0-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-128">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="fefb0-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-129">Funções</span><span class="sxs-lookup"><span data-stu-id="fefb0-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-130">Precedência do Operador</span><span class="sxs-lookup"><span data-stu-id="fefb0-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-131">Paginação</span><span class="sxs-lookup"><span data-stu-id="fefb0-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-132">Semântica de comparação</span><span class="sxs-lookup"><span data-stu-id="fefb0-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="fefb0-133">Composição de consultas aninhadas do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fefb0-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="fefb0-134">Tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="fefb0-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="fefb0-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fefb0-135">See also</span></span>

- [<span data-ttu-id="fefb0-136">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fefb0-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- <span data-ttu-id="fefb0-137">[Entity SQL Language](entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="fefb0-137">[Entity SQL Language](entity-sql-language.md)</span></span>
- <span data-ttu-id="fefb0-138">[CSDL, SSDL, and MSL Specifications](csdl-ssdl-and-msl-specifications.md) (Especificações CSDL, SSDL e MSL)</span><span class="sxs-lookup"><span data-stu-id="fefb0-138">[CSDL, SSDL, and MSL Specifications](csdl-ssdl-and-msl-specifications.md)</span></span>
