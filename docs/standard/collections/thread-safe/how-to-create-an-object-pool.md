---
title: Criar um pool de objetos usando um ConcurrentBag
ms.date: 05/01/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 64d91162b27eba80fba63761d0a926e441b63440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287855"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="92c5d-102">Criar um pool de objetos usando um ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="92c5d-102">Create an object pool by using a ConcurrentBag</span></span>

<span data-ttu-id="92c5d-103">Este exemplo mostra como usar um <xref:System.Collections.Concurrent.ConcurrentBag%601> para implementar um pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="92c5d-103">This example shows how to use a <xref:System.Collections.Concurrent.ConcurrentBag%601> to implement an object pool.</span></span> <span data-ttu-id="92c5d-104">Pools de objeto podem melhorar o desempenho do aplicativo em situações em que exigem várias instâncias de uma classe e nos quais criar ou destruir a classe é um processo caro.</span><span class="sxs-lookup"><span data-stu-id="92c5d-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="92c5d-105">Quando um programa cliente solicita um novo objeto, o pool de objetos primeiro tenta fornecer um que já foi criado e retornado ao pool.</span><span class="sxs-lookup"><span data-stu-id="92c5d-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="92c5d-106">Se nenhum estiver disponível, só então um novo objeto será criado.</span><span class="sxs-lookup"><span data-stu-id="92c5d-106">If none is available, only then is a new object created.</span></span>

<span data-ttu-id="92c5d-107">O <xref:System.Collections.Concurrent.ConcurrentBag%601> é usado para armazenar os objetos porque ele dá suporte à rápida inserção e remoção, especialmente quando o mesmo thread está adicionando e removendo itens.</span><span class="sxs-lookup"><span data-stu-id="92c5d-107">The <xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="92c5d-108">Esse exemplo poderia ser aumentado ainda mais para ser criado em torno de um <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, que a estrutura de dados do recipiente implementa, como <xref:System.Collections.Concurrent.ConcurrentQueue%601> e <xref:System.Collections.Concurrent.ConcurrentStack%601> fazem.</span><span class="sxs-lookup"><span data-stu-id="92c5d-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

> [!TIP]
> <span data-ttu-id="92c5d-109">Este artigo define como escrever sua própria implementação de um pool de objetos com um tipo simultâneo subjacente para armazenar objetos para reutilização.</span><span class="sxs-lookup"><span data-stu-id="92c5d-109">This article defines how to write your own implementation of an object pool with an underlying concurrent type to store objects for reuse.</span></span> <span data-ttu-id="92c5d-110">No entanto, o <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> tipo já existe no <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> namespace.</span><span class="sxs-lookup"><span data-stu-id="92c5d-110">However, the <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type already exists under the <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="92c5d-111">Considere o uso do tipo disponível antes de criar sua própria implementação, que inclui muitos recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="92c5d-111">Consider using the available type before creating your own implementation, which includes many additional features.</span></span>

## <a name="example"></a><span data-ttu-id="92c5d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92c5d-112">Example</span></span>

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a><span data-ttu-id="92c5d-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="92c5d-113">See also</span></span>

- [<span data-ttu-id="92c5d-114">Coleções com segurança de thread</span><span class="sxs-lookup"><span data-stu-id="92c5d-114">Thread-Safe Collections</span></span>](index.md)
