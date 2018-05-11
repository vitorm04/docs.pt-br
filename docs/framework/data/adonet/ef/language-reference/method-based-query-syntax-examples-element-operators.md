---
title: 'Exemplos de sintaxe da consulta com base em método: Operadores de elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 0933b1852d87f4f00a77aacfd9ea2cf19a3e9a1f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="4527e-102">Exemplos de sintaxe da consulta com base em método: Operadores de elemento</span><span class="sxs-lookup"><span data-stu-id="4527e-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="4527e-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.First%2A> método para consultar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="4527e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="4527e-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4527e-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4527e-105">O exemplo neste tópico usa o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="4527e-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="4527e-106">Primeiro</span><span class="sxs-lookup"><span data-stu-id="4527e-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="4527e-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4527e-107">Example</span></span>  
 <span data-ttu-id="4527e-108">O exemplo a seguir usa o <xref:System.Linq.Enumerable.First%2A> método para localizar o primeiro endereço de email que começa com 'caroline'.</span><span class="sxs-lookup"><span data-stu-id="4527e-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4527e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4527e-109">See Also</span></span>  
 [<span data-ttu-id="4527e-110">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4527e-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
