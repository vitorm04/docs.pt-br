---
title: Problemas conhecidos e considerações no LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 3945d4fc92bea2c4212da0507618203603ae8aba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780525"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="bb987-102">Problemas conhecidos e considerações no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="bb987-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="bb987-103">Esta seção fornece informações sobre problemas conhecidos com consultas do [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb987-103">This section provides information about known issues with [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
- [<span data-ttu-id="bb987-104">Consultas LINQ que não podem ser armazenados em cache</span><span class="sxs-lookup"><span data-stu-id="bb987-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="bb987-105">Informações de ordenação perdidas</span><span class="sxs-lookup"><span data-stu-id="bb987-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="bb987-106">Inteiros sem sinal não tem suportados</span><span class="sxs-lookup"><span data-stu-id="bb987-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="bb987-107">Erros de conversão de tipo</span><span class="sxs-lookup"><span data-stu-id="bb987-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="bb987-108">Referenciando variáveis não escalares não tem suportadas</span><span class="sxs-lookup"><span data-stu-id="bb987-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="bb987-109">Consultas aninhadas podem falhar com o SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="bb987-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="bb987-110">Projetando para um tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="bb987-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="bb987-111">Consultas LINQ que não podem ser armazenadas em cache</span><span class="sxs-lookup"><span data-stu-id="bb987-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="bb987-112">A partir do .NET Framework 4.5, as consultas LINQ to Entities são automaticamente armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="bb987-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="bb987-113">No entanto, as consultas LINQ to Entities que aplicam o operador `Enumerable.Contains` a coleções na memória não são armazenadas em cache automaticamente.</span><span class="sxs-lookup"><span data-stu-id="bb987-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="bb987-114">Além disso, não é permitido parametrizar coleções na memória em consultas LINQ compiladas.</span><span class="sxs-lookup"><span data-stu-id="bb987-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="bb987-115">Informações de ordenação perdidas</span><span class="sxs-lookup"><span data-stu-id="bb987-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="bb987-116">Projetar colunas em um tipo anônimo fará com que as informações de ordenação sejam perdidas em algumas consultas executadas em um banco de dados [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] definido com um nível de compatibilidade de “80".</span><span class="sxs-lookup"><span data-stu-id="bb987-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] database set to a compatibility level of "80".</span></span>  <span data-ttu-id="bb987-117">Isso ocorre quando um nome de coluna na lista order-by corresponde a um nome de coluna no seletor, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb987-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="bb987-118">Inteiros sem sinal não suportados</span><span class="sxs-lookup"><span data-stu-id="bb987-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="bb987-119">Especificando um tipo inteiro sem sinal em um [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] consulta não tem suporte porque o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] não oferece suporte a inteiros sem sinal.</span><span class="sxs-lookup"><span data-stu-id="bb987-119">Specifying an unsigned integer type in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="bb987-120">Se você especificar um inteiro sem sinal, um <xref:System.ArgumentException> exceção será gerada durante a conversão de expressão de consulta, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb987-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="bb987-121">Este exemplo consulta um pedido com a ID 48000.</span><span class="sxs-lookup"><span data-stu-id="bb987-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="bb987-122">Erros de conversão de tipos</span><span class="sxs-lookup"><span data-stu-id="bb987-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="bb987-123">No Visual Basic, quando uma propriedade é mapeada para uma coluna de tipo bit do SQL Server com um valor igual a 1 usando a função `CByte`, um <xref:System.Data.SqlClient.SqlException> é gerado com uma mensagem de “Erro de estouro aritmético".</span><span class="sxs-lookup"><span data-stu-id="bb987-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="bb987-124">O exemplo a seguir consulta a coluna `Product.MakeFlag` no banco de dados de exemplo AdventureWorks e uma exceção é gerada quando os resultados da consulta são iterados sobre.</span><span class="sxs-lookup"><span data-stu-id="bb987-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="bb987-125">Referenciando variáveis não escalares não suportadas</span><span class="sxs-lookup"><span data-stu-id="bb987-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="bb987-126">A referência a variáveis não escalares, como uma entidade, em uma consulta não é suportada.</span><span class="sxs-lookup"><span data-stu-id="bb987-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="bb987-127">Quando uma consulta desse tipo é executada, é gerada uma exceção <xref:System.NotSupportedException> com a mensagem "Não foi possível criar um valor constante de tipo `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="bb987-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="bb987-128">Apenas tipos primitivos ('como Int32, String e GUID') são suportados nesse contexto."</span><span class="sxs-lookup"><span data-stu-id="bb987-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb987-129">A referência a uma coleção de variáveis escalares é suportada.</span><span class="sxs-lookup"><span data-stu-id="bb987-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="bb987-130">Pode haver falha em consultas aninhadas com o SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="bb987-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="bb987-131">Com o SQL Server 2000, pode haver falha em consultas do LINQ to Entities se elas gerarem consultas Transact-SQL aninhadas com três ou mais níveis de profundidade.</span><span class="sxs-lookup"><span data-stu-id="bb987-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="bb987-132">Projetando para um tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="bb987-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="bb987-133">Se você definir o caminho da consulta inicial para incluir objetos relacionados usando o método <xref:System.Data.Objects.ObjectQuery%601.Include%2A> no <xref:System.Data.Objects.ObjectQuery%601> e, em seguida, usar o LINQ para projetar os objetos retornados para um tipo anônimo, os objetos especificados no método de inclusão não serão incluídos nos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="bb987-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="bb987-134">Para obter objetos relacionados, não projete tipos retornados para um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="bb987-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="bb987-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb987-135">See also</span></span>

- [<span data-ttu-id="bb987-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="bb987-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
