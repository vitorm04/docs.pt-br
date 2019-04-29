---
title: 'Exemplos de sintaxe de consulta baseada em método: Agrupamento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 8f09983aa90be666cc13ae4eba018db2ae706daa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760591"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="c8e2a-102">Exemplos de sintaxe de consulta baseada em método: Agrupamento</span><span class="sxs-lookup"><span data-stu-id="c8e2a-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="c8e2a-103">Os exemplos neste tópico mostram como usar o `GroupBy` método para consultar o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) usando a sintaxe de consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="c8e2a-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="c8e2a-104">Modelo de Vendas de exemplo AdventureWorks que é usada nesses exemplos é compilado de tabelas de contato, o endereço, do produto, de SalesOrderHeader, e o SalesOrderDetail na base de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c8e2a-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c8e2a-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="c8e2a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="c8e2a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8e2a-106">Example</span></span>  
 <span data-ttu-id="c8e2a-107">O exemplo a seguir usa o método de `GroupBy` para retornar objetos de `Address` que são agrupados pelo código postal.</span><span class="sxs-lookup"><span data-stu-id="c8e2a-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="c8e2a-108">Os resultados são projetados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="c8e2a-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="c8e2a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8e2a-109">Example</span></span>  
 <span data-ttu-id="c8e2a-110">O exemplo a seguir usa o método de `GroupBy` para retornar objetos de `Contact` que são agrupados pela primeira letra do último contato.</span><span class="sxs-lookup"><span data-stu-id="c8e2a-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="c8e2a-111">Os resultados são também classificados pela primeira letra do sobrenome e projetados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="c8e2a-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="c8e2a-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8e2a-112">Example</span></span>  
 <span data-ttu-id="c8e2a-113">O exemplo a seguir usa o método de `GroupBy` para retornar objetos de `SalesOrderHeader` que são agrupados pela identificação do cliente</span><span class="sxs-lookup"><span data-stu-id="c8e2a-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="c8e2a-114">O número de vendas para cada cliente também é retornado.</span><span class="sxs-lookup"><span data-stu-id="c8e2a-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="c8e2a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8e2a-115">See also</span></span>

- [<span data-ttu-id="c8e2a-116">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c8e2a-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
