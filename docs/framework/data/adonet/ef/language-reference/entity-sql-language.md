---
title: Linguagem Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 09ec1a5518ec0847b54394449f32b3068c811577
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140927"
---
# <a name="entity-sql-language"></a><span data-ttu-id="d70a0-102">Linguagem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d70a0-102">Entity SQL Language</span></span>
<span data-ttu-id="d70a0-103">O Entity SQL é uma linguagem de consulta independente de armazenamento semelhante ao SQL.</span><span class="sxs-lookup"><span data-stu-id="d70a0-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="d70a0-104">O Entity SQL permite que você consulte dados de entidade, como objetos ou em forma de tabela.</span><span class="sxs-lookup"><span data-stu-id="d70a0-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="d70a0-105">Você deve considerar o uso do Entity SQL nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="d70a0-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="d70a0-106">Quando uma consulta deve ser construída dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d70a0-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="d70a0-107">Nesse caso, você também deve considerar o uso dos métodos do construtor de consultas de <xref:System.Data.Objects.ObjectQuery%601>, em vez de construir uma cadeia de caracteres de consulta Entity SQL em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d70a0-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="d70a0-108">Quando você deseja definir uma consulta como parte da definição do modelo.</span><span class="sxs-lookup"><span data-stu-id="d70a0-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="d70a0-109">Somente o Entity SQL tem suporte em um modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="d70a0-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="d70a0-110">Para obter mais informações, consulte [QueryView elemento (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="d70a0-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="d70a0-111">Ao usar EntityClient para retornar dados de entidade somente leitura como conjuntos de linhas usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d70a0-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="d70a0-112">Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="d70a0-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="d70a0-113">Se você já for um especialista em linguagens de consulta baseadas em SQL, o Entity SQL poderá parecer a opção mais natural para você.</span><span class="sxs-lookup"><span data-stu-id="d70a0-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="d70a0-114">Usando Entity SQL com o provedor EntityClient</span><span class="sxs-lookup"><span data-stu-id="d70a0-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="d70a0-115">Se você desejar usar o Entity SQL com o provedor EntityClient, consulte os seguintes tópicos para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="d70a0-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="d70a0-116">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d70a0-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="d70a0-117">Como: criar uma cadeia de conexão EntityConnection</span><span class="sxs-lookup"><span data-stu-id="d70a0-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="d70a0-118">Como: executar uma consulta que retorna resultados de PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="d70a0-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="d70a0-119">Como: executar uma consulta que retorna resultados de StructuralType</span><span class="sxs-lookup"><span data-stu-id="d70a0-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="d70a0-120">Como: executar uma consulta que retorna resultados de RefType</span><span class="sxs-lookup"><span data-stu-id="d70a0-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="d70a0-121">Como: executar uma consulta que retorna tipos complexos</span><span class="sxs-lookup"><span data-stu-id="d70a0-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="d70a0-122">Como: executar uma consulta que retorna aninhados coleções</span><span class="sxs-lookup"><span data-stu-id="d70a0-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="d70a0-123">Como: executar uma consulta Entity SQL parametrizada usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="d70a0-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="d70a0-124">Como: executar um procedimento armazenado parametrizado usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="d70a0-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="d70a0-125">Como: executar uma consulta polimorfo</span><span class="sxs-lookup"><span data-stu-id="d70a0-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="d70a0-126">Como: navegar em relações com o operador navegar</span><span class="sxs-lookup"><span data-stu-id="d70a0-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="d70a0-127">Usando o Entity SQL com consultas de objetos</span><span class="sxs-lookup"><span data-stu-id="d70a0-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="d70a0-128">Se você desejar usar o Entity SQL com consultas de objetos, consulte os seguintes tópicos para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="d70a0-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="d70a0-129">Como: Executar uma consulta que retorna objetos do tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="d70a0-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [<span data-ttu-id="d70a0-130">Como: Executar uma consulta parametrizada</span><span class="sxs-lookup"><span data-stu-id="d70a0-130">How to: Execute a Parameterized Query</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [<span data-ttu-id="d70a0-131">Como: Navegar em relações usando as propriedades de navegação</span><span class="sxs-lookup"><span data-stu-id="d70a0-131">How to: Navigate Relationships Using Navigation Properties</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [<span data-ttu-id="d70a0-132">Como: Chamar uma função definida pelo usuário</span><span class="sxs-lookup"><span data-stu-id="d70a0-132">How to: Call a User-Defined Function</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [<span data-ttu-id="d70a0-133">Como: Filtrar dados</span><span class="sxs-lookup"><span data-stu-id="d70a0-133">How to: Filter Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [<span data-ttu-id="d70a0-134">Como: Classificar dados</span><span class="sxs-lookup"><span data-stu-id="d70a0-134">How to: Sort Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [<span data-ttu-id="d70a0-135">Como: Dados de grupo</span><span class="sxs-lookup"><span data-stu-id="d70a0-135">How to: Group Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [<span data-ttu-id="d70a0-136">Como: Dados de agregação</span><span class="sxs-lookup"><span data-stu-id="d70a0-136">How to: Aggregate Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [<span data-ttu-id="d70a0-137">Como: Executar uma consulta que retorna objetos de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="d70a0-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [<span data-ttu-id="d70a0-138">Como: Executar uma consulta que retorna uma coleção de tipos primitivos</span><span class="sxs-lookup"><span data-stu-id="d70a0-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [<span data-ttu-id="d70a0-139">Como: Consultar objetos relacionados em uma EntityCollection</span><span class="sxs-lookup"><span data-stu-id="d70a0-139">How to: Query Related Objects in an EntityCollection</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [<span data-ttu-id="d70a0-140">Como: A união de duas consultas de ordem</span><span class="sxs-lookup"><span data-stu-id="d70a0-140">How to: Order the Union of Two Queries</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [<span data-ttu-id="d70a0-141">Como: Paginar os resultados da consulta</span><span class="sxs-lookup"><span data-stu-id="d70a0-141">How to: Page Through Query Results</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a><span data-ttu-id="d70a0-142">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d70a0-142">In This Section</span></span>  
 [<span data-ttu-id="d70a0-143">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d70a0-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="d70a0-144">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d70a0-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="d70a0-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d70a0-145">See also</span></span>

- [<span data-ttu-id="d70a0-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d70a0-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
- [<span data-ttu-id="d70a0-147">Referência de linguagem</span><span class="sxs-lookup"><span data-stu-id="d70a0-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
