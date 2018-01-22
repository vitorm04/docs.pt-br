---
title: "Exemplos de sintaxe da consulta com base em método: Adição a operadores"
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
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b5bd7e5f86cec18f03474ac22a66199a6f95383a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="a69c3-102">Exemplos de sintaxe da consulta com base em método: Adição a operadores</span><span class="sxs-lookup"><span data-stu-id="a69c3-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="a69c3-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A> métodos para consultar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="a69c3-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="a69c3-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a69c3-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a69c3-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="a69c3-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="a69c3-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="a69c3-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="a69c3-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a69c3-107">Example</span></span>  
 <span data-ttu-id="a69c3-108">O exemplo a seguir executa um <xref:System.Linq.Enumerable.GroupJoin%2A> nas tabelas SalesOrderHeader e SalesOrderDetail para localizar o número de pedidos por cliente.</span><span class="sxs-lookup"><span data-stu-id="a69c3-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="a69c3-109">Um group join é o equivalente a um left outer join, que retorna cada elemento da primeira fonte de dados (esquerda), mesmo se nenhum elemento correlacionado estiver na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a69c3-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="a69c3-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a69c3-110">Example</span></span>  
 <span data-ttu-id="a69c3-111">O exemplo a seguir executa um <xref:System.Linq.Enumerable.GroupJoin%2A> nas tabelas Contact e SalesOrderHeader para localizar o número de pedidos por contato.</span><span class="sxs-lookup"><span data-stu-id="a69c3-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="a69c3-112">A contagem do pedido e as identificações para cada contato são exibidos.</span><span class="sxs-lookup"><span data-stu-id="a69c3-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="a69c3-113">Join</span><span class="sxs-lookup"><span data-stu-id="a69c3-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="a69c3-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a69c3-114">Example</span></span>  
 <span data-ttu-id="a69c3-115">O exemplo a seguir executa uma união sobre as tabelas de contatos e de SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="a69c3-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="a69c3-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a69c3-116">Example</span></span>  
 <span data-ttu-id="a69c3-117">O exemplo a seguir executa uma união sobre as tabelas de contatos e de SalesOrderHeader, agrupamento os resultados pela identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="a69c3-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="a69c3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a69c3-118">See Also</span></span>  
 [<span data-ttu-id="a69c3-119">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="a69c3-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
