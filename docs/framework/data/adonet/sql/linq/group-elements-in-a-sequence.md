---
title: Agrupar os elementos em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: bc490b579e841a0e9b3724fe0e8789cc9411683d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782182"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="339f5-102">Agrupar os elementos em uma sequência</span><span class="sxs-lookup"><span data-stu-id="339f5-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="339f5-103">O operador de <xref:System.Linq.Enumerable.GroupBy%2A> agrupa elementos de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="339f5-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="339f5-104">Os exemplos usam o base de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="339f5-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="339f5-105">Valores nulos de coluna em consultas de <xref:System.Linq.Enumerable.GroupBy%2A> podem lançar as vezes <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="339f5-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="339f5-106">Para obter mais informações, consulte a seção "GroupBy InvalidOperationException" de [solução de problemas](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="339f5-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="339f5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-107">Example</span></span>  
 <span data-ttu-id="339f5-108">O exemplo a seguir divide `Products` por `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="339f5-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="339f5-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-109">Example</span></span>  
 <span data-ttu-id="339f5-110">Os seguintes usa <xref:System.Linq.Enumerable.Max%2A> de exemplo encontrar o preço unitário máximo para cada `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="339f5-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="339f5-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-111">Example</span></span>  
 <span data-ttu-id="339f5-112">Os seguintes o exemplo usa especificam intermediária para localizar `UnitPrice` médio para cada `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="339f5-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="339f5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-113">Example</span></span>  
 <span data-ttu-id="339f5-114">Os seguintes usa <xref:System.Linq.Queryable.Sum%2A> de exemplo encontrar `UnitPrice` total para cada `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="339f5-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="339f5-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-115">Example</span></span>  
 <span data-ttu-id="339f5-116">Os seguintes usa <xref:System.Linq.Queryable.Count%2A> de exemplo encontrar o número de `Products` descontinuado em cada `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="339f5-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="339f5-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-117">Example</span></span>  
 <span data-ttu-id="339f5-118">O exemplo a seguir usa uma cláusula de `where` para localizar todas as categorias que tem pelo menos 10 produtos.</span><span class="sxs-lookup"><span data-stu-id="339f5-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="339f5-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-119">Example</span></span>  
 <span data-ttu-id="339f5-120">O exemplo a seguir agrupa produtos por `CategoryID` e por `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="339f5-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="339f5-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-121">Example</span></span>  
 <span data-ttu-id="339f5-122">O exemplo a seguir retorna duas sequências de produtos.</span><span class="sxs-lookup"><span data-stu-id="339f5-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="339f5-123">A primeira sequência contém classes com preço unitário menor ou igual a 10.</span><span class="sxs-lookup"><span data-stu-id="339f5-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="339f5-124">A segunda sequência contém classes com o preço unitário maior que 10.</span><span class="sxs-lookup"><span data-stu-id="339f5-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="339f5-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339f5-125">Example</span></span>  
 <span data-ttu-id="339f5-126">O operador de <xref:System.Linq.Queryable.GroupBy%2A> pode levar apenas um único argumento principal.</span><span class="sxs-lookup"><span data-stu-id="339f5-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="339f5-127">Se você precisará se agrupar por mais de uma chave, você deve criar um tipo anônimo, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="339f5-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="339f5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="339f5-128">See also</span></span>

- [<span data-ttu-id="339f5-129">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="339f5-129">Query Examples</span></span>](query-examples.md)
- <span data-ttu-id="339f5-130">[Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="339f5-130">[Downloading Sample Databases](downloading-sample-databases.md)</span></span>
