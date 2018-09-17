---
title: Como criar um pool de objetos usando um ConcurrentBag
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bc0c6bebbab6e84c165f41300a4cb16c8746a07
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45597262"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="fce54-102">Como criar um pool de objetos usando um ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="fce54-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="fce54-103">Este exemplo mostra como usar um recipiente simultâneo para implementar um pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="fce54-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="fce54-104">Pools de objeto podem melhorar o desempenho do aplicativo em situações em que exigem várias instâncias de uma classe e nos quais criar ou destruir a classe é um processo caro.</span><span class="sxs-lookup"><span data-stu-id="fce54-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="fce54-105">Quando um programa cliente solicita um novo objeto, o pool de objetos primeiro tenta fornecer um que já foi criado e retornado ao pool.</span><span class="sxs-lookup"><span data-stu-id="fce54-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="fce54-106">Se nenhum estiver disponível, só então um novo objeto será criado.</span><span class="sxs-lookup"><span data-stu-id="fce54-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="fce54-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> é usado para armazenar os objetos porque ele dá suporte à inserção e remoção rápidas, principalmente quando o mesmo thread está adicionando e removendo itens.</span><span class="sxs-lookup"><span data-stu-id="fce54-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="fce54-108">Esse exemplo poderia ser aumentado ainda mais para ser criado em torno de um <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, que a estrutura de dados do recipiente implementa, como <xref:System.Collections.Concurrent.ConcurrentQueue%601> e <xref:System.Collections.Concurrent.ConcurrentStack%601> fazem.</span><span class="sxs-lookup"><span data-stu-id="fce54-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fce54-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fce54-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="fce54-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fce54-110">See also</span></span>

- [<span data-ttu-id="fce54-111">Coleções Thread-Safe</span><span class="sxs-lookup"><span data-stu-id="fce54-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
