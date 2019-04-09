---
title: Interface IHostMemoryManager
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137339"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="02764-102">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="02764-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="02764-103">Fornece métodos que permitem que o common language runtime (CLR) para fazer solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual padrão do Win32.</span><span class="sxs-lookup"><span data-stu-id="02764-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02764-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="02764-104">Methods</span></span>  
  
|<span data-ttu-id="02764-105">Método</span><span class="sxs-lookup"><span data-stu-id="02764-105">Method</span></span>|<span data-ttu-id="02764-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="02764-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02764-107">Método AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="02764-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="02764-108">Notifica o host que o common language runtime (CLR) adquiriu a memória especificada do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="02764-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="02764-109">Método CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="02764-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="02764-110">Obtém um ponteiro de interface para um [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instância que é usada para solicitar as alocações de memória de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="02764-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="02764-111">Método GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="02764-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="02764-112">Obtém a quantidade de memória física que está sendo usada, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="02764-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="02764-113">Método NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="02764-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="02764-114">Notifica o host que o CLR irá tentar usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="02764-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="02764-115">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="02764-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="02764-116">Registra um ponteiro para uma função de retorno de chamada que o host chama para notificar o CLR da carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="02764-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="02764-117">Método ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="02764-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="02764-118">Notifica o host que o CLR foi concluída usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="02764-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="02764-119">Método VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="02764-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="02764-120">Serve como um wrapper lógico para a função Win32 correspondente, que reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="02764-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="02764-121">Método VirtualFree</span><span class="sxs-lookup"><span data-stu-id="02764-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="02764-122">Serve como um wrapper lógico para a função Win32 correspondente, o que libera, desfaz a confirmação, ou libera e anulações de confirmação de uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="02764-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="02764-123">Método VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="02764-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="02764-124">Serve como um wrapper lógico para a função Win32 correspondente, que altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="02764-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="02764-125">Método VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="02764-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="02764-126">Serve como um wrapper lógico para a função Win32 correspondente, que recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="02764-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02764-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="02764-127">Remarks</span></span>  
 `IHostMemoryManager` <span data-ttu-id="02764-128">também fornece métodos para o CLR para obter um ponteiro por meio do qual fazer solicitações de memória no heap e para obter o nível de pressão de memória no processo, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="02764-128">also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02764-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02764-129">Requirements</span></span>  
 <span data-ttu-id="02764-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02764-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02764-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02764-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02764-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="02764-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="02764-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="02764-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="02764-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02764-134">See also</span></span>

- [<span data-ttu-id="02764-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="02764-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="02764-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="02764-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
