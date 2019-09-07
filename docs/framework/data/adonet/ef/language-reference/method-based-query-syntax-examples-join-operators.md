---
title: 'Exemplos de sintaxe de consulta baseada em método: Operadores de junção'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: c7dafae846a30424f008cce5f597efbdefa4bdf8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397354"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="10fe5-102">Exemplos de sintaxe de consulta baseada em método: Operadores de junção</span><span class="sxs-lookup"><span data-stu-id="10fe5-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="10fe5-103">Os exemplos neste tópico demonstram como usar os métodos <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A> para consultar o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de consulta baseada em método.</span><span class="sxs-lookup"><span data-stu-id="10fe5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="10fe5-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="10fe5-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="10fe5-105">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="10fe5-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="10fe5-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="10fe5-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="10fe5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10fe5-107">Example</span></span>  
 <span data-ttu-id="10fe5-108">O exemplo a seguir executa um <xref:System.Linq.Enumerable.GroupJoin%2A> nas tabelas SalesOrderHeader e SalesOrderDetail para localizar o número de pedidos por cliente.</span><span class="sxs-lookup"><span data-stu-id="10fe5-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="10fe5-109">Um group join é o equivalente a um left outer join, que retorna cada elemento da primeira fonte de dados (esquerda), mesmo se nenhum elemento correlacionado estiver na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="10fe5-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="10fe5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10fe5-110">Example</span></span>  
 <span data-ttu-id="10fe5-111">O exemplo a seguir executa um <xref:System.Linq.Enumerable.GroupJoin%2A> nas tabelas Contact e SalesOrderHeader para localizar o número de pedidos por contato.</span><span class="sxs-lookup"><span data-stu-id="10fe5-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="10fe5-112">A contagem do pedido e as identificações para cada contato são exibidos.</span><span class="sxs-lookup"><span data-stu-id="10fe5-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="10fe5-113">Join</span><span class="sxs-lookup"><span data-stu-id="10fe5-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="10fe5-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10fe5-114">Example</span></span>  
 <span data-ttu-id="10fe5-115">O exemplo a seguir executa uma união sobre as tabelas de contatos e de SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="10fe5-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="10fe5-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10fe5-116">Example</span></span>  
 <span data-ttu-id="10fe5-117">O exemplo a seguir executa uma união sobre as tabelas de contatos e de SalesOrderHeader, agrupamento os resultados pela identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="10fe5-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="10fe5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10fe5-118">See also</span></span>

- [<span data-ttu-id="10fe5-119">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="10fe5-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
