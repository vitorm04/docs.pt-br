---
title: "Exemplos de sintaxe da consulta com base em método: Classificação"
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
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7797d3cacc38954b419efec34e1f811a265083df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="1e449-102">Exemplos de sintaxe da consulta com base em método: Classificação</span><span class="sxs-lookup"><span data-stu-id="1e449-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="1e449-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.ThenBy%2A> método para consultar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="1e449-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="1e449-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1e449-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1e449-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="1e449-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="1e449-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="1e449-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="1e449-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e449-107">Example</span></span>  
 <span data-ttu-id="1e449-108">O exemplo a seguir na sintaxe da consulta com base em método usa <xref:System.Linq.Queryable.OrderBy%2A> e <xref:System.Linq.Queryable.ThenBy%2A> para retornar uma lista de contatos ordenados por sobrenome e em seguida pelo nome.</span><span class="sxs-lookup"><span data-stu-id="1e449-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="1e449-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="1e449-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="1e449-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e449-110">Example</span></span>  
 <span data-ttu-id="1e449-111">O seguinte exemplo usa os métodos de <xref:System.Linq.Queryable.OrderBy%2A> e de <xref:System.Linq.Queryable.ThenByDescending%2A> para o primeiro tipo pelo custo da tabela e em seguida, executar uma descida meio de nomes do produto.</span><span class="sxs-lookup"><span data-stu-id="1e449-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1e449-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e449-112">See Also</span></span>  
 [<span data-ttu-id="1e449-113">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1e449-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
