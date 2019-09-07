---
title: 'Exemplos de sintaxe de expressão de consulta: Agrupamento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: c9876c72a03f7827ec4b28d78f06ed372460caff
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398461"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="fcd10-102">Exemplos de sintaxe de expressão de consulta: Agrupamento</span><span class="sxs-lookup"><span data-stu-id="fcd10-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="fcd10-103">Os exemplos neste tópico demonstram como usar o `GroupBy` método para consultar o modelo de [vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="fcd10-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="fcd10-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fcd10-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fcd10-105">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="fcd10-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="fcd10-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcd10-106">Example</span></span>  
 <span data-ttu-id="fcd10-107">O exemplo a seguir retorna os objetos `Address` agrupados pelo código postal.</span><span class="sxs-lookup"><span data-stu-id="fcd10-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="fcd10-108">Os resultados são projetados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="fcd10-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="fcd10-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcd10-109">Example</span></span>  
 <span data-ttu-id="fcd10-110">O exemplo a seguir retorna os objetos `Contact` agrupados pela primeira letra do sobrenome do contato.</span><span class="sxs-lookup"><span data-stu-id="fcd10-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="fcd10-111">Os resultados são também classificados pela primeira letra do sobrenome e projetados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="fcd10-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="fcd10-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcd10-112">Example</span></span>  
 <span data-ttu-id="fcd10-113">O exemplo a seguir retorna os objetos `SalesOrderHeader` agrupados pela ID do cliente.</span><span class="sxs-lookup"><span data-stu-id="fcd10-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="fcd10-114">O número de vendas para cada cliente também é retornado.</span><span class="sxs-lookup"><span data-stu-id="fcd10-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="fcd10-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcd10-115">See also</span></span>

- [<span data-ttu-id="fcd10-116">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="fcd10-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
