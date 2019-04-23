---
title: Converter um tipo genérico a um IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d75c9b9123b52b3e241bea1bbd1d302c406715e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190366"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="1c809-102">Converter um tipo genérico a um IEnumerable</span><span class="sxs-lookup"><span data-stu-id="1c809-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="1c809-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> para retornar o argumento tipado como `IEnumerable`genérico.</span><span class="sxs-lookup"><span data-stu-id="1c809-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c809-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c809-104">Example</span></span>  
 <span data-ttu-id="1c809-105">Nesse exemplo, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (usando `Query`genérico padrão) tentaria converter a consulta SQL e executados no servidor.</span><span class="sxs-lookup"><span data-stu-id="1c809-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="1c809-106">Mas a cláusula de `where` referencia um método do lado do cliente definido pelo usuário (`isValidProduct`), que não pode ser convertido para SQL.</span><span class="sxs-lookup"><span data-stu-id="1c809-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="1c809-107">A solução é especificar a implementação genérica do lado do cliente de <xref:System.Collections.Generic.IEnumerable%601> de `where` para substituir <xref:System.Linq.IQueryable%601>genérico.</span><span class="sxs-lookup"><span data-stu-id="1c809-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="1c809-108">Você faz isso chamando o operador de <xref:System.Linq.Enumerable.AsEnumerable%2A> .</span><span class="sxs-lookup"><span data-stu-id="1c809-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="1c809-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c809-109">See also</span></span>

- [<span data-ttu-id="1c809-110">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="1c809-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
