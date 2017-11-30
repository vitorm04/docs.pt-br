---
title: Como controlar a ordem em uma consulta PLINQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="62ee8-102">Como controlar a ordem em uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="62ee8-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="62ee8-103">Estes exemplos mostram como controlar a ordem em uma consulta PLINQ usando o <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> método de extensão.</span><span class="sxs-lookup"><span data-stu-id="62ee8-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="62ee8-104">Esses exemplos destinam-se principalmente para demonstrar o uso e podem ou não podem ser executada mais rápido do que o LINQ sequencial equivalente para consultas de objetos.</span><span class="sxs-lookup"><span data-stu-id="62ee8-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62ee8-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62ee8-105">Example</span></span>  
 <span data-ttu-id="62ee8-106">O exemplo a seguir preserva a ordenação da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="62ee8-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="62ee8-107">Isso às vezes é necessário; Por exemplo, alguns operadores de consulta exigem uma sequência ordenada de origem para produzir resultados corretos.</span><span class="sxs-lookup"><span data-stu-id="62ee8-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="62ee8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62ee8-108">Example</span></span>  
 <span data-ttu-id="62ee8-109">A exemplo a seguir mostra alguns operadores sequência cuja origem provavelmente deve ser ordenados de consulta.</span><span class="sxs-lookup"><span data-stu-id="62ee8-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="62ee8-110">Esses operadores funcionará em sequências não ordenadas, mas eles podem produzir resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="62ee8-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="62ee8-111">Para executar esse método, cole-a classe de PLINQDataSample o [exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) do projeto e pressione F5.</span><span class="sxs-lookup"><span data-stu-id="62ee8-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62ee8-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62ee8-112">Example</span></span>  
 <span data-ttu-id="62ee8-113">O exemplo a seguir mostra como preservar a ordenação para a primeira parte de uma consulta, em seguida, remover a ordenação para aumentar o desempenho de uma cláusula join e reaplique pedidos à sequência de resultados final.</span><span class="sxs-lookup"><span data-stu-id="62ee8-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="62ee8-114">Para executar esse método, cole-a classe de PLINQDataSample o [exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) do projeto e pressione F5.</span><span class="sxs-lookup"><span data-stu-id="62ee8-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ee8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62ee8-115">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="62ee8-116">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="62ee8-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
