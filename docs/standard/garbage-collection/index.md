---
title: Coleta de lixo do .NET
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: ef7e078c6ef2f0b4081c49aa0db09316e79f0702
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286048"
---
# <a name="garbage-collection"></a><span data-ttu-id="e27d3-102">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="e27d3-102">Garbage collection</span></span>

<span data-ttu-id="e27d3-103">O coletor de lixo do .NET gerencia a alocação e a liberação de memória para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e27d3-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="e27d3-104">Toda vez que você cria um novo objeto, o Common Language Runtime aloca memória para o objeto do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e27d3-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="e27d3-105">Desde que exista espaço de endereço disponível no heap gerenciado, o runtime continua alocando espaço para novos objetos.</span><span class="sxs-lookup"><span data-stu-id="e27d3-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="e27d3-106">No entanto, a memória não é infinita.</span><span class="sxs-lookup"><span data-stu-id="e27d3-106">However, memory is not infinite.</span></span> <span data-ttu-id="e27d3-107">No fim das contas, o coletor de lixo deve realizar uma coleta para liberar algum espaço na memória.</span><span class="sxs-lookup"><span data-stu-id="e27d3-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="e27d3-108">O mecanismo de otimização do coletor de lixo determina o melhor momento para executar uma coleta com base nas alocações que estão sendo feitas.</span><span class="sxs-lookup"><span data-stu-id="e27d3-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="e27d3-109">Quando o coletor de lixo executa uma coleta, ele verifica se há objetos no heap gerenciado que não estão mais sendo usados pelo aplicativo e realiza as operações necessárias para recuperar sua memória.</span><span class="sxs-lookup"><span data-stu-id="e27d3-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e27d3-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e27d3-110">In this section</span></span>
  
|<span data-ttu-id="e27d3-111">Title</span><span class="sxs-lookup"><span data-stu-id="e27d3-111">Title</span></span>|<span data-ttu-id="e27d3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e27d3-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e27d3-113">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="e27d3-113">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="e27d3-114">Descreve como funciona a coleta de lixo, como os objetos são alocados no heap gerenciado e outros conceitos principais.</span><span class="sxs-lookup"><span data-stu-id="e27d3-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="e27d3-115">Coleta de lixo de estação de trabalho ou de servidor</span><span class="sxs-lookup"><span data-stu-id="e27d3-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="e27d3-116">Descreve as diferenças entre a coleta de lixo da estação de trabalho para aplicativos cliente e a coleta de lixo do servidor para aplicativos de servidor.</span><span class="sxs-lookup"><span data-stu-id="e27d3-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="e27d3-117">Coleta de lixo em segundo plano</span><span class="sxs-lookup"><span data-stu-id="e27d3-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="e27d3-118">Descreve a coleta de lixo em segundo plano, que é a coleção de objetos de geração 0 e 1 enquanto a coleta de geração 2 está em andamento.</span><span class="sxs-lookup"><span data-stu-id="e27d3-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="e27d3-119">O heap de objetos grandes</span><span class="sxs-lookup"><span data-stu-id="e27d3-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="e27d3-120">Descreve o LOH (heap de objeto grande) e como os objetos grandes são coletados por lixo.</span><span class="sxs-lookup"><span data-stu-id="e27d3-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="e27d3-121">Coleta de lixo e desempenho</span><span class="sxs-lookup"><span data-stu-id="e27d3-121">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="e27d3-122">Descreve as verificações de desempenho que você pode usar para diagnosticar problemas de desempenho e de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e27d3-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="e27d3-123">Coletas induzidas</span><span class="sxs-lookup"><span data-stu-id="e27d3-123">Induced collections</span></span>](induced.md)|<span data-ttu-id="e27d3-124">Descreve como fazer uma coleta de lixo ocorrer.</span><span class="sxs-lookup"><span data-stu-id="e27d3-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="e27d3-125">Modos de latência</span><span class="sxs-lookup"><span data-stu-id="e27d3-125">Latency modes</span></span>](latency.md)|<span data-ttu-id="e27d3-126">Descreve os modos de determinam o grau de intrusão da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e27d3-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="e27d3-127">Otimização da hospedagem Web compartilhada</span><span class="sxs-lookup"><span data-stu-id="e27d3-127">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="e27d3-128">Descreve como otimizar a coleta de lixo em servidores compartilhados por vários sites pequenos.</span><span class="sxs-lookup"><span data-stu-id="e27d3-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="e27d3-129">Notificações da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="e27d3-129">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="e27d3-130">Descreve como determinar quando uma coleta de lixo completa está se aproximando e quando ela é concluída.</span><span class="sxs-lookup"><span data-stu-id="e27d3-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="e27d3-131">Monitoramento de recursos do domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="e27d3-131">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="e27d3-132">Descreve como monitorar o uso de CPU e memória por um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e27d3-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="e27d3-133">Referências fracas</span><span class="sxs-lookup"><span data-stu-id="e27d3-133">Weak references</span></span>](weak-references.md)|<span data-ttu-id="e27d3-134">Descreve os recursos que permitem que um objeto seja, simultaneamente, coletado pelo coletor de lixo e acessado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e27d3-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="e27d3-135">Referência</span><span class="sxs-lookup"><span data-stu-id="e27d3-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="e27d3-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="e27d3-136">See also</span></span>

- [<span data-ttu-id="e27d3-137">Limpar recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="e27d3-137">Clean up unmanaged resources</span></span>](unmanaged.md)
