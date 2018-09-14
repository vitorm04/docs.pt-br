---
title: Coleta de Lixo
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f61b63f78ea3c6131d4d1ab4e421be25149035b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521262"
---
# <a name="garbage-collection"></a><span data-ttu-id="7eb48-102">Coleta de Lixo</span><span class="sxs-lookup"><span data-stu-id="7eb48-102">Garbage Collection</span></span>
<span data-ttu-id="7eb48-103">O coletor de lixo do .NET gerencia a alocação e a liberação de memória para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb48-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="7eb48-104">Toda vez que você cria um novo objeto, o Common Language Runtime aloca memória para o objeto do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7eb48-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="7eb48-105">Desde que exista espaço de endereço disponível no heap gerenciado, o tempo de execução continua alocando espaço para novos objetos.</span><span class="sxs-lookup"><span data-stu-id="7eb48-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="7eb48-106">No entanto, a memória não é infinita.</span><span class="sxs-lookup"><span data-stu-id="7eb48-106">However, memory is not infinite.</span></span> <span data-ttu-id="7eb48-107">No fim das contas, o coletor de lixo deve realizar uma coleta para liberar algum espaço na memória.</span><span class="sxs-lookup"><span data-stu-id="7eb48-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="7eb48-108">O mecanismo de otimização do coletor de lixo determina o melhor momento para executar uma coleta com base nas alocações que estão sendo feitas.</span><span class="sxs-lookup"><span data-stu-id="7eb48-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="7eb48-109">Quando o coletor de lixo executa uma coleta, ele verifica se há objetos no heap gerenciado que não estão mais sendo usados pelo aplicativo e realiza as operações necessárias para recuperar sua memória.</span><span class="sxs-lookup"><span data-stu-id="7eb48-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="7eb48-110">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="7eb48-110">Related Topics</span></span>  
  
|<span data-ttu-id="7eb48-111">Título</span><span class="sxs-lookup"><span data-stu-id="7eb48-111">Title</span></span>|<span data-ttu-id="7eb48-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7eb48-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7eb48-113">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="7eb48-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="7eb48-114">Descreve como funciona a coleta de lixo, como os objetos são alocados no heap gerenciado e outros conceitos principais.</span><span class="sxs-lookup"><span data-stu-id="7eb48-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="7eb48-115">Coleta de lixo e desempenho</span><span class="sxs-lookup"><span data-stu-id="7eb48-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="7eb48-116">Descreve as verificações de desempenho que você pode usar para diagnosticar problemas de desempenho e de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7eb48-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="7eb48-117">Coletas Induzidas</span><span class="sxs-lookup"><span data-stu-id="7eb48-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="7eb48-118">Descreve como fazer uma coleta de lixo ocorrer.</span><span class="sxs-lookup"><span data-stu-id="7eb48-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="7eb48-119">Modos de latência</span><span class="sxs-lookup"><span data-stu-id="7eb48-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="7eb48-120">Descreve os modos de determinam o grau de intrusão da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7eb48-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="7eb48-121">Otimização para hospedagem na Web compartilhada</span><span class="sxs-lookup"><span data-stu-id="7eb48-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="7eb48-122">Descreve como otimizar a coleta de lixo em servidores compartilhados por vários sites pequenos.</span><span class="sxs-lookup"><span data-stu-id="7eb48-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="7eb48-123">Notificações de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="7eb48-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="7eb48-124">Descreve como determinar quando uma coleta de lixo completa está se aproximando e quando ela é concluída.</span><span class="sxs-lookup"><span data-stu-id="7eb48-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="7eb48-125">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="7eb48-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="7eb48-126">Descreve como monitorar o uso de CPU e memória por um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb48-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="7eb48-127">Referências fracas</span><span class="sxs-lookup"><span data-stu-id="7eb48-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="7eb48-128">Descreve os recursos que permitem que um objeto seja, simultaneamente, coletado pelo coletor de lixo e acessado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb48-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="7eb48-129">Referência</span><span class="sxs-lookup"><span data-stu-id="7eb48-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="7eb48-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eb48-130">See also</span></span>

- [<span data-ttu-id="7eb48-131">Limpando recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="7eb48-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
