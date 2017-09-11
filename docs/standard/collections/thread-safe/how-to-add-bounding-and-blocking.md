---
title: "Como adicionar a funcionalidade de delimitação e bloqueio a uma coleção"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3258534cb0bf67b180080eca4f7cefc65c609fa4
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="20d6c-102">Como adicionar a funcionalidade de delimitação e bloqueio a uma coleção</span><span class="sxs-lookup"><span data-stu-id="20d6c-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="20d6c-103">Este exemplo mostra como adicionar a funcionalidade de delimitação e de bloqueio a uma classe de coleção personalizada por meio da implementação da interface <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> na classe e do uso de uma instância da classe como o mecanismo de armazenamento interno para um <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="20d6c-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>.</span></span> <span data-ttu-id="20d6c-104">Para obter mais informações sobre delimitação e bloqueio, veja [Visão geral de BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="20d6c-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20d6c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20d6c-105">Example</span></span>  
 <span data-ttu-id="20d6c-106">A classe de coleção personalizada é uma fila de prioridade básica na qual os níveis de prioridade são representados como uma matriz de objetos <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="20d6c-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> objects.</span></span> <span data-ttu-id="20d6c-107">Nenhuma solicitação adicional é executada dentro de cada fila.</span><span class="sxs-lookup"><span data-stu-id="20d6c-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="20d6c-108">No código do cliente, três tarefas são iniciadas.</span><span class="sxs-lookup"><span data-stu-id="20d6c-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="20d6c-109">A primeira tarefa apenas monitora a digitação no teclado para permitir o cancelamento a qualquer momento durante a execução.</span><span class="sxs-lookup"><span data-stu-id="20d6c-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="20d6c-110">A segunda tarefa é o thread produtor; ele adiciona novos itens na coleção de bloqueio e atribui uma prioridade com base em um valor aleatório a cada item.</span><span class="sxs-lookup"><span data-stu-id="20d6c-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="20d6c-111">A terceira tarefa remove itens da coleção assim que eles ficarem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="20d6c-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="20d6c-112">Você pode ajustar o comportamento do aplicativo fazendo com que um dos threads seja executado mais rapidamente do que o outro.</span><span class="sxs-lookup"><span data-stu-id="20d6c-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="20d6c-113">Se o produtor for executado mais rapidamente, você observará que a funcionalidade delimitadora como a coleta de bloqueio impedirá que itens sejam adicionados se ela já contiver o número de itens especificado no construtor.</span><span class="sxs-lookup"><span data-stu-id="20d6c-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="20d6c-114">Se o consumidor for executado mais rapidamente, você observará a funcionalidade de bloqueio enquanto o consumidor aguarda que um novo item seja adicionado.</span><span class="sxs-lookup"><span data-stu-id="20d6c-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 <span data-ttu-id="20d6c-115">[!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]</span><span class="sxs-lookup"><span data-stu-id="20d6c-115">[!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]</span></span>  
  
 <span data-ttu-id="20d6c-116">Por padrão, o armazenamento para um <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> é <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="20d6c-116">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d6c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20d6c-117">See Also</span></span>  
 [<span data-ttu-id="20d6c-118">Coleções Thread-Safe</span><span class="sxs-lookup"><span data-stu-id="20d6c-118">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)

