---
title: 'Como: Usar matrizes de coleções de bloqueio em um pipeline'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4667d78fdf91a3e62c22d88c7cbe9effaae57d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627194"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="87aa8-102">Como: Usar matrizes de coleções de bloqueio em um pipeline</span><span class="sxs-lookup"><span data-stu-id="87aa8-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="87aa8-103">O exemplo a seguir mostra como usar matrizes de objetos <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> com métodos estáticos como <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> e <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> para implementar transferência de dados rápida e flexível entre componentes.</span><span class="sxs-lookup"><span data-stu-id="87aa8-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87aa8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87aa8-104">Example</span></span>  
 <span data-ttu-id="87aa8-105">O exemplo a seguir demonstra uma implementação de pipeline básica na qual cada objeto está pegando dados simultaneamente da coleção de entrada, transformando-os e passando-os à coleção de saída.</span><span class="sxs-lookup"><span data-stu-id="87aa8-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="87aa8-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87aa8-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="87aa8-107">Coleções Thread-Safe</span><span class="sxs-lookup"><span data-stu-id="87aa8-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
