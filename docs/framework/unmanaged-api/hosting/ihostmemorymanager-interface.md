---
title: Interface IHostMemoryManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager
helpviewer_keywords: IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b39a43874bc1808928f21e0a35638aae9a99ca8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="443b0-102">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="443b0-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="443b0-103">Fornece métodos que permitem que o common language runtime (CLR) para fazer solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual padrão do Win32.</span><span class="sxs-lookup"><span data-stu-id="443b0-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="443b0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="443b0-104">Methods</span></span>  
  
|<span data-ttu-id="443b0-105">Método</span><span class="sxs-lookup"><span data-stu-id="443b0-105">Method</span></span>|<span data-ttu-id="443b0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="443b0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="443b0-107">Método AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="443b0-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="443b0-108">Notifica o host que o common language runtime (CLR) adquiriu a memória especificada do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="443b0-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="443b0-109">Método CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="443b0-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="443b0-110">Obtém um ponteiro de interface para um [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instância que é usada para solicitar as alocações de memória de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="443b0-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="443b0-111">Método GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="443b0-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="443b0-112">Obtém a quantidade de memória física que está sendo usada, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="443b0-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="443b0-113">Método NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="443b0-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="443b0-114">Notifica o host que o CLR vai tentar usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="443b0-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="443b0-115">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="443b0-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="443b0-116">Registra um ponteiro para uma função de retorno de chamada que invoca o host para notificar o CLR da carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="443b0-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="443b0-117">Método ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="443b0-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="443b0-118">Notifica o host que o CLR foi concluída usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="443b0-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="443b0-119">Método VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="443b0-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="443b0-120">Serve como um wrapper lógico para a função Win32 correspondente, que reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="443b0-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="443b0-121">Método VirtualFree</span><span class="sxs-lookup"><span data-stu-id="443b0-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="443b0-122">Serve como um wrapper lógico para a função Win32 correspondente, o que libera, decommits, ou libera e decommits uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="443b0-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="443b0-123">Método VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="443b0-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="443b0-124">Serve como um wrapper lógico para a função Win32 correspondente, que altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="443b0-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="443b0-125">Método VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="443b0-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="443b0-126">Serve como um wrapper lógico para a função Win32 correspondente, que recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="443b0-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="443b0-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="443b0-127">Remarks</span></span>  
 <span data-ttu-id="443b0-128">`IHostMemoryManager`também fornece métodos para o CLR para obter um ponteiro por meio do qual fazer solicitações de memória no heap e para obter o nível de pressão de memória no processo, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="443b0-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="443b0-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="443b0-129">Requirements</span></span>  
 <span data-ttu-id="443b0-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="443b0-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="443b0-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="443b0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="443b0-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="443b0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="443b0-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="443b0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443b0-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="443b0-134">See Also</span></span>  
 [<span data-ttu-id="443b0-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="443b0-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="443b0-136">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="443b0-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
