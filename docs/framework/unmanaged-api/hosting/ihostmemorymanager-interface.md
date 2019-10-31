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
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128656"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="64e79-102">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="64e79-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="64e79-103">Fornece métodos que permitem que o Common Language Runtime (CLR) faça solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual Win32 padrão.</span><span class="sxs-lookup"><span data-stu-id="64e79-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64e79-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="64e79-104">Methods</span></span>  
  
|<span data-ttu-id="64e79-105">Método</span><span class="sxs-lookup"><span data-stu-id="64e79-105">Method</span></span>|<span data-ttu-id="64e79-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="64e79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64e79-107">Método AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="64e79-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="64e79-108">Notifica o host de que o Common Language Runtime (CLR) adquiriu a memória especificada do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="64e79-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="64e79-109">Método CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="64e79-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="64e79-110">Obtém um ponteiro de interface para uma instância de [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) que é usada para solicitar alocações de memória de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="64e79-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="64e79-111">Método GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="64e79-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="64e79-112">Obtém a quantidade de memória física que está sendo usada no momento, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="64e79-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="64e79-113">Método NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="64e79-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="64e79-114">Notifica o host que o CLR vai tentar usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="64e79-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="64e79-115">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="64e79-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="64e79-116">Registra um ponteiro para uma função de retorno de chamada que o host chama para notificar o CLR sobre a carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="64e79-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="64e79-117">Método ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="64e79-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="64e79-118">Notifica o host que o CLR concluiu usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="64e79-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="64e79-119">Método VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="64e79-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="64e79-120">Serve como um wrapper lógico para a função Win32 correspondente, que reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="64e79-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="64e79-121">Método VirtualFree</span><span class="sxs-lookup"><span data-stu-id="64e79-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="64e79-122">Serve como um wrapper lógico para a função Win32 correspondente, que libera, desconfirma ou libera e desconfirma uma região de páginas dentro do espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="64e79-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="64e79-123">Método VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="64e79-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="64e79-124">Serve como um wrapper lógico para a função Win32 correspondente, que altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="64e79-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="64e79-125">Método VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="64e79-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="64e79-126">Serve como um wrapper lógico para a função Win32 correspondente, que recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="64e79-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64e79-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="64e79-127">Remarks</span></span>  
 <span data-ttu-id="64e79-128">o `IHostMemoryManager` também fornece métodos para o CLR obter um ponteiro por meio do qual fazer solicitações de memória no heap e obter o nível de pressão de memória no processo, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="64e79-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e79-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64e79-129">Requirements</span></span>  
 <span data-ttu-id="64e79-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64e79-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e79-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="64e79-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64e79-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="64e79-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64e79-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64e79-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e79-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64e79-134">See also</span></span>

- [<span data-ttu-id="64e79-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="64e79-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="64e79-136">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="64e79-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
