---
title: "Exemplos de sintaxe da expressão de consulta: Operadores de elemento"
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
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 846344bf5e8005473fe7db8217228cd33179a206
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="4f8d5-102">Exemplos de sintaxe da expressão de consulta: Operadores de elemento</span><span class="sxs-lookup"><span data-stu-id="4f8d5-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="4f8d5-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.First%2A> método para consultar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using the query expression syntax.</span></span> <span data-ttu-id="4f8d5-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4f8d5-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="4f8d5-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="4f8d5-106">Primeiro</span><span class="sxs-lookup"><span data-stu-id="4f8d5-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="4f8d5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f8d5-107">Example</span></span>  
 <span data-ttu-id="4f8d5-108">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro contato cujo nome é “Brooke”.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="4f8d5-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f8d5-109">See Also</span></span>  
 [<span data-ttu-id="4f8d5-110">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4f8d5-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
