---
title: Resultados da Consulta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32133d1b6fce619fb9990ab89820b7f19b6a5926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="query-results"></a><span data-ttu-id="eb168-102">Resultados da Consulta</span><span class="sxs-lookup"><span data-stu-id="eb168-102">Query Results</span></span>
<span data-ttu-id="eb168-103">Depois que uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] é convertida para o comando árvores e executada, os resultados da consulta geralmente são retornados como um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="eb168-103">After a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is converted to command trees and executed, the query results are usually returned as one of the following:</span></span>  
  
-   <span data-ttu-id="eb168-104">Uma coleção de zero ou mais objetos de entidade tipados ou uma projeção de tipos complexos no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="eb168-104">A collection of zero or more typed entity objects or a projection of complex types in the conceptual model.</span></span>  
  
-   <span data-ttu-id="eb168-105">Tipos de CLR suportados pelo modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="eb168-105">CLR types supported by the conceptual model.</span></span>  
  
-   <span data-ttu-id="eb168-106">Coleções internas.</span><span class="sxs-lookup"><span data-stu-id="eb168-106">Inline collections.</span></span>  
  
-   <span data-ttu-id="eb168-107">Tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="eb168-107">Anonymous types.</span></span>  
  
 <span data-ttu-id="eb168-108">Quando a consulta executar contra a fonte de dados, os resultados são materializados em tipos de CLR e retornados para o cliente.</span><span class="sxs-lookup"><span data-stu-id="eb168-108">When the query has executed against the data source, the results are materialized into CLR types and returned to the client.</span></span> <span data-ttu-id="eb168-109">Qualquer materialization de objeto é executado por [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb168-109">All object materialization is performed by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="eb168-110">Todos os erros que resultarem de uma incapacidade mapeamento entre [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] e CLR causarão exceções a ser geradas durante o materialization de objeto.</span><span class="sxs-lookup"><span data-stu-id="eb168-110">Any errors that result from an inability to map between the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] and the CLR will cause exceptions to be thrown during object materialization.</span></span>  
  
 <span data-ttu-id="eb168-111">Se a execução da consulta retorna tipos primitivos de modelo conceitual, os resultados consistem de tipos de CLR que são autônomos e desconectado de [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb168-111">If the query execution returns primitive conceptual model types, the results consist of CLR types that are stand-alone and disconnected from the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="eb168-112">No entanto, se a consulta retorna uma coleção de objetos de entidade tipados, representado por <xref:System.Data.Objects.ObjectQuery%601>, os tipos são controlados pelo contexto de objeto.</span><span class="sxs-lookup"><span data-stu-id="eb168-112">However, if the query returns a collection of typed entity objects, represented by <xref:System.Data.Objects.ObjectQuery%601>, those types are tracked by the object context.</span></span> <span data-ttu-id="eb168-113">Todo o comportamento de objeto (como coleções de pai/filho, o controle de alterações, polimorfismo e assim por diante) são definidos no [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb168-113">All object behavior (such as child/parent collections, change tracking, polymorphism, and so on) are as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="eb168-114">Essa funcionalidade pode ser usada em sua capacidade, conforme definido no [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb168-114">This functionality can be used in its capacity, as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="eb168-115">Para obter mais informações, consulte [trabalhando com objetos](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="eb168-115">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="eb168-116">Os tipos de Estrutura retornados de consultas (como tipos anônimos e tipos complexos anuláveis) podem ser de valor de `null` .</span><span class="sxs-lookup"><span data-stu-id="eb168-116">Struct types returned from queries (such as anonymous types and nullable complex types) can be of `null` value.</span></span> <span data-ttu-id="eb168-117">Uma propriedade de <xref:System.Data.Objects.DataClasses.EntityCollection%601> de uma entidade retornado também pode ser o valor de `null` .</span><span class="sxs-lookup"><span data-stu-id="eb168-117">An <xref:System.Data.Objects.DataClasses.EntityCollection%601> property of a returned entity can also be of `null` value.</span></span> <span data-ttu-id="eb168-118">Isso pode resultar de projetar a propriedade de coleção de uma entidade que é o valor de `null` , como chamar <xref:System.Linq.Queryable.FirstOrDefault%2A> em <xref:System.Data.Objects.ObjectQuery%601> que não tiver nenhum elemento.</span><span class="sxs-lookup"><span data-stu-id="eb168-118">This can result from projecting the collection property of an entity that is of `null` value, such as calling <xref:System.Linq.Queryable.FirstOrDefault%2A> on an <xref:System.Data.Objects.ObjectQuery%601> that has no elements.</span></span>  
  
 <span data-ttu-id="eb168-119">Em determinadas situações, uma consulta pode parecer para produzir um resultado materializado durante sua execução, mas a consulta será executada no servidor e o objeto de entidade será materializado nunca em CLR.</span><span class="sxs-lookup"><span data-stu-id="eb168-119">In certain situations, a query might appear to generate a materialized result during its execution, but the query will be executed on the server and the entity object will never be materialized in the CLR.</span></span> <span data-ttu-id="eb168-120">Isso pode causar problemas se você estiver como efeitos colaterais de materialization de objeto.</span><span class="sxs-lookup"><span data-stu-id="eb168-120">This can cause problems if you are depending on side effects of object materialization.</span></span>  
  
 <span data-ttu-id="eb168-121">O exemplo a seguir contém uma classe personalizada, `MyContact`, com uma propriedade de `LastName` .</span><span class="sxs-lookup"><span data-stu-id="eb168-121">The following example contains a custom class, `MyContact`, with a `LastName` property.</span></span> <span data-ttu-id="eb168-122">Quando a propriedade de `LastName` é definida, uma variável de `count` é incrementado.</span><span class="sxs-lookup"><span data-stu-id="eb168-122">When the `LastName` property is set, a `count` variable is incremented.</span></span> <span data-ttu-id="eb168-123">Se você executa as duas consultas a seguir, a primeira consulta incrementará `count` quando a segunda consulta não.</span><span class="sxs-lookup"><span data-stu-id="eb168-123">If you execute the two following queries, the first query will increment `count` while the second query will not.</span></span> <span data-ttu-id="eb168-124">Isso ocorre porque na segunda consulta a propriedade de `LastName` é projetada de resultados e a classe de `MyContact` nunca é criada, porque não é necessário executar a consulta no armazenamento.</span><span class="sxs-lookup"><span data-stu-id="eb168-124">This is because in the second query the `LastName` property is projected from the results and the `MyContact` class is never created, because it is not required to execute the query on the store.</span></span>  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
