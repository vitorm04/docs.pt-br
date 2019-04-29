---
title: 'Exemplos de sintaxe de consulta baseada em método: Conversão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: bf6c889fff2635cd50597e72151c46fbb4d9b97d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760578"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="b5eff-102">Exemplos de sintaxe de consulta baseada em método: Conversão</span><span class="sxs-lookup"><span data-stu-id="b5eff-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="b5eff-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> e <xref:System.Linq.Enumerable.ToList%2A> métodos para consultar o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) usando a sintaxe de consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="b5eff-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="b5eff-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b5eff-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b5eff-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="b5eff-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="b5eff-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="b5eff-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="b5eff-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5eff-107">Example</span></span>  
 <span data-ttu-id="b5eff-108">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.ToArray%2A> para avaliar imediatamente uma sequência em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="b5eff-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="b5eff-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="b5eff-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="b5eff-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5eff-110">Example</span></span>  
 <span data-ttu-id="b5eff-111">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.ToDictionary%2A> para avaliar imediatamente uma sequência e uma expressão chave relacionadas em um dicionário.</span><span class="sxs-lookup"><span data-stu-id="b5eff-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="b5eff-112">ToList</span><span class="sxs-lookup"><span data-stu-id="b5eff-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="b5eff-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5eff-113">Example</span></span>  
 <span data-ttu-id="b5eff-114">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.ToList%2A> para avaliar imediatamente uma sequência em <xref:System.Collections.Generic.List%601>, onde `T` é do tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="b5eff-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="b5eff-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5eff-115">See also</span></span>

- [<span data-ttu-id="b5eff-116">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b5eff-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
