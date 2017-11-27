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
ms.openlocfilehash: 415539be0dbed8e0cf3f9d6e5c79bf4cfac09fe2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="11ee4-102">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="11ee4-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="11ee4-103">Fornece métodos que permitem que o common language runtime (CLR) para fazer solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual padrão do Win32.</span><span class="sxs-lookup"><span data-stu-id="11ee4-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11ee4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="11ee4-104">Methods</span></span>  
  
|<span data-ttu-id="11ee4-105">Método</span><span class="sxs-lookup"><span data-stu-id="11ee4-105">Method</span></span>|<span data-ttu-id="11ee4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="11ee4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11ee4-107">Método AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="11ee4-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="11ee4-108">Notifica o host que o common language runtime (CLR) adquiriu a memória especificada do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="11ee4-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="11ee4-109">Método CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="11ee4-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="11ee4-110">Obtém um ponteiro de interface para um [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instância que é usada para solicitar as alocações de memória de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="11ee4-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="11ee4-111">Método getMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="11ee4-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="11ee4-112">Obtém a quantidade de memória física que está sendo usada, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="11ee4-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="11ee4-113">Método NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="11ee4-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="11ee4-114">Notifica o host que o CLR vai tentar usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="11ee4-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="11ee4-115">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="11ee4-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="11ee4-116">Registra um ponteiro para uma função de retorno de chamada que invoca o host para notificar o CLR da carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="11ee4-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="11ee4-117">Método ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="11ee4-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="11ee4-118">Notifica o host que o CLR foi concluída usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="11ee4-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="11ee4-119">Método VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="11ee4-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="11ee4-120">Serve como um wrapper lógico para a função Win32 correspondente, que reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="11ee4-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="11ee4-121">Método VirtualFree</span><span class="sxs-lookup"><span data-stu-id="11ee4-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="11ee4-122">Serve como um wrapper lógico para a função Win32 correspondente, o que libera, decommits, ou libera e decommits uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="11ee4-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="11ee4-123">Método VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="11ee4-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="11ee4-124">Serve como um wrapper lógico para a função Win32 correspondente, que altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="11ee4-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="11ee4-125">Método VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="11ee4-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="11ee4-126">Serve como um wrapper lógico para a função Win32 correspondente, que recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="11ee4-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11ee4-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="11ee4-127">Remarks</span></span>  
 <span data-ttu-id="11ee4-128">`IHostMemoryManager`também fornece métodos para o CLR para obter um ponteiro por meio do qual fazer solicitações de memória no heap e para obter o nível de pressão de memória no processo, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="11ee4-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11ee4-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11ee4-129">Requirements</span></span>  
 <span data-ttu-id="11ee4-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11ee4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11ee4-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11ee4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11ee4-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="11ee4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11ee4-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11ee4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ee4-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11ee4-134">See Also</span></span>  
 [<span data-ttu-id="11ee4-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="11ee4-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="11ee4-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="11ee4-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
