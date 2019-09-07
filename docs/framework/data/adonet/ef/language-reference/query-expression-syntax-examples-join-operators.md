---
title: 'Exemplos de sintaxe de expressão de consulta: Operadores de junção'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: b1a85dda5d860445174a46d1bc4738962d588369
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398443"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="aef55-102">Exemplos de sintaxe de expressão de consulta: Operadores de junção</span><span class="sxs-lookup"><span data-stu-id="aef55-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="aef55-103">A junção é uma operação importante em consultas que usam fontes de dados de destino que não têm nenhuma relação navegável entre si, como, por exemplo, as tabelas do banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="aef55-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="aef55-104">Uma junção de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="aef55-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="aef55-105">Para obter mais informações, consulte [visão geral de operadores de consulta padrão](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="aef55-105">For more information, see [Standard Query Operators Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="aef55-106">Os exemplos neste tópico demonstram como usar os métodos <xref:System.Linq.Enumerable.GroupJoin%2A> e <xref:System.Linq.Enumerable.Join%2A> para consultar o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="aef55-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="aef55-107">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="aef55-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aef55-108">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="aef55-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="aef55-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="aef55-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="aef55-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aef55-110">Example</span></span>  
 <span data-ttu-id="aef55-111">O exemplo a seguir executa um <xref:System.Linq.Enumerable.GroupJoin%2A> nas tabelas SalesOrderHeader e SalesOrderDetail para localizar o número de pedidos por cliente.</span><span class="sxs-lookup"><span data-stu-id="aef55-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="aef55-112">Um group join é o equivalente a um left outer join, que retorna cada elemento da primeira fonte de dados (esquerda), mesmo se nenhum elemento correlacionado estiver na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="aef55-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="aef55-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aef55-113">Example</span></span>  
 <span data-ttu-id="aef55-114">O exemplo a seguir executa um <xref:System.Linq.Enumerable.GroupJoin%2A> nas tabelas Contact e SalesOrderHeader para localizar o número de pedidos por contato.</span><span class="sxs-lookup"><span data-stu-id="aef55-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="aef55-115">A contagem do pedido e as identificações para cada contato são exibidos.</span><span class="sxs-lookup"><span data-stu-id="aef55-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="aef55-116">Join</span><span class="sxs-lookup"><span data-stu-id="aef55-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="aef55-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aef55-117">Example</span></span>  
 <span data-ttu-id="aef55-118">O exemplo a seguir realiza uma união das tabelas SalesOrderHeader e SalesOrderDetail para obter pedidos online do mês de agosto.</span><span class="sxs-lookup"><span data-stu-id="aef55-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="aef55-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aef55-119">See also</span></span>

- [<span data-ttu-id="aef55-120">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="aef55-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
