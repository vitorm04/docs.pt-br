---
title: 'Exemplos de sintaxe de consulta com base em método: Divisão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 2155d0cb9aa47e5940974db92077b51f8139e09d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536068"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="27d4d-102">Exemplos de sintaxe de consulta com base em método: Divisão</span><span class="sxs-lookup"><span data-stu-id="27d4d-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="27d4d-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.Skip%2A>, e <xref:System.Linq.Enumerable.Take%2A> métodos para consultar o [modelo de vendas AdventureWorks](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="27d4d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="27d4d-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="27d4d-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="27d4d-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="27d4d-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="27d4d-106">Skip</span><span class="sxs-lookup"><span data-stu-id="27d4d-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="27d4d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27d4d-107">Example</span></span>  
 <span data-ttu-id="27d4d-108">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter mas todos os cinco primeiros contatos da tabela de contatos.</span><span class="sxs-lookup"><span data-stu-id="27d4d-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="27d4d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27d4d-109">Example</span></span>  
 <span data-ttu-id="27d4d-110">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter todos mas os dois primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="27d4d-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="27d4d-111">Take</span><span class="sxs-lookup"><span data-stu-id="27d4d-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="27d4d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27d4d-112">Example</span></span>  
 <span data-ttu-id="27d4d-113">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter apenas os cinco primeiros contatos da tabela de contatos.</span><span class="sxs-lookup"><span data-stu-id="27d4d-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="27d4d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27d4d-114">Example</span></span>  
 <span data-ttu-id="27d4d-115">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter os três primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="27d4d-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="27d4d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27d4d-116">See also</span></span>
- [<span data-ttu-id="27d4d-117">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="27d4d-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
