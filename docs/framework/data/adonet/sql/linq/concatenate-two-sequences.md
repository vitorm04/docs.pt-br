---
title: Concatenar duas sequências
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: a2f2510cb334f4e22a7b0c6015a0a93b4dc11579
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142773"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="64284-102">Concatenar duas sequências</span><span class="sxs-lookup"><span data-stu-id="64284-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="64284-103">Use o operador de <xref:System.Linq.Queryable.Concat%2A> para concatenar duas sequências.</span><span class="sxs-lookup"><span data-stu-id="64284-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="64284-104">O operador de <xref:System.Linq.Queryable.Concat%2A> é definido para os multisets ordenados onde os pedidos do receptor e argumento são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="64284-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="64284-105">Ordenação em SQL é a etapa final antes que os resultados são gerados.</span><span class="sxs-lookup"><span data-stu-id="64284-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="64284-106">Por esse motivo, o operador de <xref:System.Linq.Queryable.Concat%2A> é implementado usando `UNION ALL` e não preserva a ordem dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="64284-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="64284-107">Para certificar-se de ordenação está correta nos resultados, certifique-se pedir explicitamente os resultados.</span><span class="sxs-lookup"><span data-stu-id="64284-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64284-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64284-108">Example</span></span>  
 <span data-ttu-id="64284-109">Este exemplo usa <xref:System.Linq.Queryable.Concat%2A> para retornar uma sequência de todos os números de `Customer` e de telefone e fax de `Employee` .</span><span class="sxs-lookup"><span data-stu-id="64284-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="64284-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64284-110">Example</span></span>  
 <span data-ttu-id="64284-111">Este exemplo usa <xref:System.Linq.Queryable.Concat%2A> para retornar uma sequência mapeamentos de qualquer nome de `Customer` e de `Employee` e de número de telefone.</span><span class="sxs-lookup"><span data-stu-id="64284-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="64284-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64284-112">See also</span></span>

- [<span data-ttu-id="64284-113">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="64284-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="64284-114">Conversão padrão de operador de consulta</span><span class="sxs-lookup"><span data-stu-id="64284-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
