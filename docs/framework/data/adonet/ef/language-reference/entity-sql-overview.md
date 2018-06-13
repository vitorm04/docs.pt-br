---
title: Visão geral da Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e7cadbd357ab96d67c6d1f1e49ba0d8b3883bf3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760733"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="be2a5-102">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="be2a5-102">Entity SQL Overview</span></span>
<span data-ttu-id="be2a5-103">A linguagem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é semelhante à SQL e permite que você consulte modelos conceituais no [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be2a5-103">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="be2a5-104">Modelos conceituais representam os dados em entidades e relações, e [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite consultar essas entidades e relações em um formato que é familiar para aqueles que usaram SQL.</span><span class="sxs-lookup"><span data-stu-id="be2a5-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="be2a5-105">O [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] funciona com provedores de dados específicos ao armazenamento para converter a linguagem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] genérica em consultas específicas ao armazenamento.</span><span class="sxs-lookup"><span data-stu-id="be2a5-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="be2a5-106">O provedor EntityClient permite executar um comando [!INCLUDE[esql](../../../../../../includes/esql-md.md)] em um modelo de entidade e retornar tipos de dados ricos que incluem resultados escalares, conjuntos de resultados e gráficos de objeto.</span><span class="sxs-lookup"><span data-stu-id="be2a5-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="be2a5-107">Ao criar objetos <xref:System.Data.EntityClient.EntityCommand>, você pode especificar um nome de procedimento armazenado ou o texto de uma consulta atribuindo uma cadeia de caracteres de consulta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a sua propriedade <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be2a5-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="be2a5-108">O <xref:System.Data.EntityClient.EntityDataReader> expõe os resultados da execução de um <xref:System.Data.EntityClient.EntityCommand> em um EDM.</span><span class="sxs-lookup"><span data-stu-id="be2a5-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="be2a5-109">Para executar o comando que retorna <xref:System.Data.EntityClient.EntityDataReader>, chame <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2a5-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="be2a5-110">Além do provedor EntityClient, o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] permite que você use a linguagem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para executar consultas em um modelo conceitual e retornar dados como os objetos CLR fortemente tipados que são instâncias de tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="be2a5-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="be2a5-111">Para obter mais informações, consulte [trabalhando com objetos](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="be2a5-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="be2a5-112">Esta seção fornece informações conceituais sobre a linguagem [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be2a5-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be2a5-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="be2a5-113">In This Section</span></span>  
 [<span data-ttu-id="be2a5-114">Diferenças entre o Entity SQL e o Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="be2a5-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="be2a5-115">Referência rápida de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="be2a5-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="be2a5-116">Sistema de tipos</span><span class="sxs-lookup"><span data-stu-id="be2a5-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-117">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="be2a5-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-118">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="be2a5-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-119">Cache de plano de consulta</span><span class="sxs-lookup"><span data-stu-id="be2a5-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-120">Namespaces</span><span class="sxs-lookup"><span data-stu-id="be2a5-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-121">Identificadores</span><span class="sxs-lookup"><span data-stu-id="be2a5-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-122">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="be2a5-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-123">Variáveis</span><span class="sxs-lookup"><span data-stu-id="be2a5-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-124">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="be2a5-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-125">Literais</span><span class="sxs-lookup"><span data-stu-id="be2a5-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-126">Literais nulos e inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="be2a5-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-127">Conjunto de caracteres de entrada</span><span class="sxs-lookup"><span data-stu-id="be2a5-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-128">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="be2a5-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-129">Funções</span><span class="sxs-lookup"><span data-stu-id="be2a5-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-130">Precedência do Operador</span><span class="sxs-lookup"><span data-stu-id="be2a5-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-131">Paginação</span><span class="sxs-lookup"><span data-stu-id="be2a5-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-132">Semântica de comparação</span><span class="sxs-lookup"><span data-stu-id="be2a5-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="be2a5-133">Composição de consultas aninhadas do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="be2a5-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="be2a5-134">Tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="be2a5-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="be2a5-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be2a5-135">See Also</span></span>  
 [<span data-ttu-id="be2a5-136">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="be2a5-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 <span data-ttu-id="be2a5-137">[Entity SQL Language](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="be2a5-137">[Entity SQL Language](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>  
 <span data-ttu-id="be2a5-138">[CSDL, SSDL, and MSL Specifications](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md) (Especificações CSDL, SSDL e MSL)</span><span class="sxs-lookup"><span data-stu-id="be2a5-138">[CSDL, SSDL, and MSL Specifications](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)</span></span>
