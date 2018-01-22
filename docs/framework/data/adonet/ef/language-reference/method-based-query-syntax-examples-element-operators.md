---
title: "Exemplos de sintaxe da consulta com base em método: Operadores de elemento"
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
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b1a5cda6597940bbf99f50c325532d8b50fad5f0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="5f488-102">Exemplos de sintaxe da consulta com base em método: Operadores de elemento</span><span class="sxs-lookup"><span data-stu-id="5f488-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="5f488-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.First%2A> método para consultar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="5f488-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="5f488-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5f488-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5f488-105">O exemplo neste tópico usa o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="5f488-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="5f488-106">Primeiro</span><span class="sxs-lookup"><span data-stu-id="5f488-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="5f488-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f488-107">Example</span></span>  
 <span data-ttu-id="5f488-108">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.First%2A> para localizar o primeiro endereço de email que começa com “caroline”.</span><span class="sxs-lookup"><span data-stu-id="5f488-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first e-mail address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="5f488-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f488-109">See Also</span></span>  
 [<span data-ttu-id="5f488-110">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5f488-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
