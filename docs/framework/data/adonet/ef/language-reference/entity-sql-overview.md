---
title: Visão geral da Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150370"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="a688b-102">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a688b-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a688b-103">é uma linguagem semelhante ao SQL que permite consultar modelos conceituais no Framework entity.</span><span class="sxs-lookup"><span data-stu-id="a688b-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="a688b-104">Os modelos conceituais representam dados [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como entidades e relacionamentos, e permite que você consulte essas entidades e relacionamentos em um formato familiar para aqueles que usaram SQL.</span><span class="sxs-lookup"><span data-stu-id="a688b-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="a688b-105">O Entity Framework trabalha com provedores [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de dados específicos de armazenamento para traduzir consultas genéricas em especificações de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="a688b-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="a688b-106">O provedor EntityClient permite executar um comando [!INCLUDE[esql](../../../../../../includes/esql-md.md)] em um modelo de entidade e retornar tipos de dados ricos que incluem resultados escalares, conjuntos de resultados e gráficos de objeto.</span><span class="sxs-lookup"><span data-stu-id="a688b-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="a688b-107">Ao criar objetos <xref:System.Data.EntityClient.EntityCommand>, você pode especificar um nome de procedimento armazenado ou o texto de uma consulta atribuindo uma cadeia de caracteres de consulta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a sua propriedade <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a688b-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a688b-108">O <xref:System.Data.EntityClient.EntityDataReader> expõe os resultados da execução de um <xref:System.Data.EntityClient.EntityCommand> em um EDM.</span><span class="sxs-lookup"><span data-stu-id="a688b-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="a688b-109">Para executar o comando que retorna <xref:System.Data.EntityClient.EntityDataReader>, chame <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="a688b-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="a688b-110">Além do provedor EntityClient, o EntityFramework [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite que você use para executar consultas contra um modelo conceitual e retornar dados como objetos CLR fortemente digitados que são instâncias de tipos de entidades.</span><span class="sxs-lookup"><span data-stu-id="a688b-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="a688b-111">Para obter mais informações, consulte [Trabalhando com objetos](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="a688b-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="a688b-112">Esta seção fornece informações conceituais sobre a linguagem [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a688b-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a688b-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a688b-113">In This Section</span></span>  
 [<span data-ttu-id="a688b-114">Como o Entity SQL difere do Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a688b-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="a688b-115">Referência rápida de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a688b-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="a688b-116">Sistema de tipo</span><span class="sxs-lookup"><span data-stu-id="a688b-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="a688b-117">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="a688b-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="a688b-118">Construir tipos</span><span class="sxs-lookup"><span data-stu-id="a688b-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="a688b-119">Cache de plano de consulta</span><span class="sxs-lookup"><span data-stu-id="a688b-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="a688b-120">Namespaces</span><span class="sxs-lookup"><span data-stu-id="a688b-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="a688b-121">Identificadores</span><span class="sxs-lookup"><span data-stu-id="a688b-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="a688b-122">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a688b-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="a688b-123">Variáveis</span><span class="sxs-lookup"><span data-stu-id="a688b-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="a688b-124">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="a688b-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="a688b-125">Literais</span><span class="sxs-lookup"><span data-stu-id="a688b-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="a688b-126">Literais nulos e inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="a688b-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="a688b-127">Conjunto de caracteres de entrada</span><span class="sxs-lookup"><span data-stu-id="a688b-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="a688b-128">Expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="a688b-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="a688b-129">Funções</span><span class="sxs-lookup"><span data-stu-id="a688b-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="a688b-130">Precedência de operador</span><span class="sxs-lookup"><span data-stu-id="a688b-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="a688b-131">Paginação</span><span class="sxs-lookup"><span data-stu-id="a688b-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="a688b-132">Semântica de comparação</span><span class="sxs-lookup"><span data-stu-id="a688b-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="a688b-133">Composta consultas aninhadas Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a688b-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="a688b-134">Tipos estruturados que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="a688b-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a688b-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="a688b-135">See also</span></span>

- [<span data-ttu-id="a688b-136">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a688b-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- <span data-ttu-id="a688b-137">[Entity SQL Language](entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="a688b-137">[Entity SQL Language](entity-sql-language.md)</span></span>
- [<span data-ttu-id="a688b-138">Especificações de CSDL, SSDL e MSL</span><span class="sxs-lookup"><span data-stu-id="a688b-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
