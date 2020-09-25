---
title: 'Exemplos de sintaxe da consulta com base em método: Divisão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 659c05f261b854b1f2bb9bc3bce7c2889650571f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191886"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="bb0d1-102">Exemplos de sintaxe da consulta com base em método: Divisão</span><span class="sxs-lookup"><span data-stu-id="bb0d1-102">Method-Based Query Syntax Examples: Partitioning</span></span>

<span data-ttu-id="bb0d1-103">Os exemplos neste tópico demonstram como usar os <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.Take%2A> métodos e para consultar o modelo de [vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="bb0d1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="bb0d1-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bb0d1-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="bb0d1-105">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="bb0d1-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="bb0d1-106">Ignorar</span><span class="sxs-lookup"><span data-stu-id="bb0d1-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="bb0d1-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb0d1-107">Example</span></span>  

 <span data-ttu-id="bb0d1-108">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter mas todos os cinco primeiros contatos da tabela de contatos.</span><span class="sxs-lookup"><span data-stu-id="bb0d1-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="bb0d1-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb0d1-109">Example</span></span>  

 <span data-ttu-id="bb0d1-110">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter todos mas os dois primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="bb0d1-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="bb0d1-111">Take</span><span class="sxs-lookup"><span data-stu-id="bb0d1-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="bb0d1-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb0d1-112">Example</span></span>  

 <span data-ttu-id="bb0d1-113">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter apenas os cinco primeiros contatos da tabela de contatos.</span><span class="sxs-lookup"><span data-stu-id="bb0d1-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="bb0d1-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb0d1-114">Example</span></span>  

 <span data-ttu-id="bb0d1-115">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter os três primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="bb0d1-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="bb0d1-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="bb0d1-116">See also</span></span>

- [<span data-ttu-id="bb0d1-117">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="bb0d1-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
