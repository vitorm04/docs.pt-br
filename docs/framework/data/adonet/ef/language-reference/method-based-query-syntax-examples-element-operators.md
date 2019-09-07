---
title: 'Exemplos de sintaxe de consulta baseada em método: Operadores de elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 7add62a2792a0fc82346851b7dd835aad5082742
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397456"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="6ddde-102">Exemplos de sintaxe de consulta baseada em método: Operadores de elemento</span><span class="sxs-lookup"><span data-stu-id="6ddde-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="6ddde-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.First%2A> método para consultar o modelo de [vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de consulta baseada em método.</span><span class="sxs-lookup"><span data-stu-id="6ddde-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="6ddde-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6ddde-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6ddde-105">O exemplo neste tópico usa as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="6ddde-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="6ddde-106">First</span><span class="sxs-lookup"><span data-stu-id="6ddde-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="6ddde-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ddde-107">Example</span></span>  
 <span data-ttu-id="6ddde-108">O exemplo a seguir usa <xref:System.Linq.Enumerable.First%2A> o método para localizar o primeiro endereço de email que começa com ' Carolina '.</span><span class="sxs-lookup"><span data-stu-id="6ddde-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="6ddde-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ddde-109">See also</span></span>

- [<span data-ttu-id="6ddde-110">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="6ddde-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
