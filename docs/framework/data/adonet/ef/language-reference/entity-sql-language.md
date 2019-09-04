---
title: Linguagem Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251013"
---
# <a name="entity-sql-language"></a><span data-ttu-id="91df9-102">Linguagem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="91df9-102">Entity SQL Language</span></span>
<span data-ttu-id="91df9-103">O Entity SQL é uma linguagem de consulta independente de armazenamento semelhante ao SQL.</span><span class="sxs-lookup"><span data-stu-id="91df9-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="91df9-104">O Entity SQL permite que você consulte dados de entidade, como objetos ou em forma de tabela.</span><span class="sxs-lookup"><span data-stu-id="91df9-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="91df9-105">Você deve considerar o uso do Entity SQL nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="91df9-105">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="91df9-106">Quando uma consulta deve ser construída dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91df9-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="91df9-107">Nesse caso, você também deve considerar o uso dos métodos do construtor de consultas de <xref:System.Data.Objects.ObjectQuery%601>, em vez de construir uma cadeia de caracteres de consulta Entity SQL em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91df9-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="91df9-108">Quando você deseja definir uma consulta como parte da definição do modelo.</span><span class="sxs-lookup"><span data-stu-id="91df9-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="91df9-109">Somente o Entity SQL tem suporte em um modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="91df9-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="91df9-110">Para obter mais informações, consulte [elemento QueryView (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="91df9-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="91df9-111">Ao usar EntityClient para retornar dados de entidade somente leitura como conjuntos de linhas usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="91df9-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="91df9-112">Para obter mais informações, consulte [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="91df9-112">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="91df9-113">Se você já for um especialista em linguagens de consulta baseadas em SQL, o Entity SQL poderá parecer a opção mais natural para você.</span><span class="sxs-lookup"><span data-stu-id="91df9-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="91df9-114">Usando Entity SQL com o provedor EntityClient</span><span class="sxs-lookup"><span data-stu-id="91df9-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="91df9-115">Se você desejar usar o Entity SQL com o provedor EntityClient, consulte os seguintes tópicos para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="91df9-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="91df9-116">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="91df9-116">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="91df9-117">Como: Criar uma cadeia de conexão de EntityConnection</span><span class="sxs-lookup"><span data-stu-id="91df9-117">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="91df9-118">Como: Executar uma consulta que retorna os resultados de Primitivatype</span><span class="sxs-lookup"><span data-stu-id="91df9-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="91df9-119">Como: Executar uma consulta que retorna resultados de Estruturaistype</span><span class="sxs-lookup"><span data-stu-id="91df9-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="91df9-120">Como: Executar uma consulta que retorna resultados de RefType</span><span class="sxs-lookup"><span data-stu-id="91df9-120">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="91df9-121">Como: Executar uma consulta que retorna tipos complexos</span><span class="sxs-lookup"><span data-stu-id="91df9-121">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="91df9-122">Como: Executar uma consulta que retorna coleções aninhadas</span><span class="sxs-lookup"><span data-stu-id="91df9-122">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="91df9-123">Como: Executar uma consulta de Entity SQL parametrizada usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="91df9-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="91df9-124">Como: Executar um procedimento armazenado com parâmetros usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="91df9-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="91df9-125">Como: Executar uma consulta polimórfica</span><span class="sxs-lookup"><span data-stu-id="91df9-125">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="91df9-126">Como: Navegar pelas relações com o operador Navigate</span><span class="sxs-lookup"><span data-stu-id="91df9-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="91df9-127">Usando o Entity SQL com consultas de objetos</span><span class="sxs-lookup"><span data-stu-id="91df9-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="91df9-128">Se você desejar usar o Entity SQL com consultas de objetos, consulte os seguintes tópicos para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="91df9-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="91df9-129">[Como: Executar uma consulta que retorna objetos de tipo de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-129">[How to: Execute a Query that Returns Entity Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-130">[Como: Executar uma consulta parametrizada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-130">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-131">[Como: Navegar pelas relações usando as propriedades de navegação](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-131">[How to: Navigate Relationships Using Navigation Properties](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-132">[Como: Chamar uma função definida pelo usuário](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-132">[How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-133">[Como: Filtrar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-133">[How to: Filter Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-134">[Como: Classificar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-134">[How to: Sort Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-135">[Como: Agrupar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-135">[How to: Group Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-136">[Como: Agregar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-136">[How to: Aggregate Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-137">[Como: Executar uma consulta que retorna objetos de tipo anônimo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-137">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-138">[Como: Executar uma consulta que retorna uma coleção de tipos primitivos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-138">[How to: Execute a Query that Returns a Collection of Primitive Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-139">[Como: Consultar objetos relacionados em uma EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-139">[How to: Query Related Objects in an EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-140">[Como: Ordenar a União de duas consultas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-140">[How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="91df9-141">[Como: Página por meio de resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91df9-141">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91df9-142">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="91df9-142">In This Section</span></span>  
 [<span data-ttu-id="91df9-143">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="91df9-143">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="91df9-144">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="91df9-144">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="91df9-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91df9-145">See also</span></span>

- [<span data-ttu-id="91df9-146">Entity Framework do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="91df9-146">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="91df9-147">Referência de Linguagem</span><span class="sxs-lookup"><span data-stu-id="91df9-147">Language Reference</span></span>](index.md)
