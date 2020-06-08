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
ms.openlocfilehash: 09b4a06892cdc450eed9dead503a990b6f19804e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501502"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="886a4-102">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="886a4-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="886a4-103">Fornece métodos que permitem que o Common Language Runtime (CLR) faça solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual Win32 padrão.</span><span class="sxs-lookup"><span data-stu-id="886a4-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="886a4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="886a4-104">Methods</span></span>  
  
|<span data-ttu-id="886a4-105">Método</span><span class="sxs-lookup"><span data-stu-id="886a4-105">Method</span></span>|<span data-ttu-id="886a4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="886a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="886a4-107">Método AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="886a4-107">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="886a4-108">Notifica o host de que o Common Language Runtime (CLR) adquiriu a memória especificada do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="886a4-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="886a4-109">Método CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="886a4-109">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="886a4-110">Obtém um ponteiro de interface para uma instância de [IHostMAlloc](ihostmalloc-interface.md) que é usada para solicitar alocações de memória de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="886a4-110">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="886a4-111">Método GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="886a4-111">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="886a4-112">Obtém a quantidade de memória física que está sendo usada no momento, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="886a4-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="886a4-113">Método NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="886a4-113">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="886a4-114">Notifica o host que o CLR vai tentar usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="886a4-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="886a4-115">Método RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="886a4-115">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="886a4-116">Registra um ponteiro para uma função de retorno de chamada que o host chama para notificar o CLR sobre a carga de memória atual no computador.</span><span class="sxs-lookup"><span data-stu-id="886a4-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="886a4-117">Método ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="886a4-117">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="886a4-118">Notifica o host que o CLR concluiu usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="886a4-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="886a4-119">Método VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="886a4-119">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="886a4-120">Serve como um wrapper lógico para a função Win32 correspondente, que reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="886a4-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="886a4-121">Método VirtualFree</span><span class="sxs-lookup"><span data-stu-id="886a4-121">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="886a4-122">Serve como um wrapper lógico para a função Win32 correspondente, que libera, desconfirma ou libera e desconfirma uma região de páginas dentro do espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="886a4-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="886a4-123">Método VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="886a4-123">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="886a4-124">Serve como um wrapper lógico para a função Win32 correspondente, que altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="886a4-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="886a4-125">Método VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="886a4-125">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="886a4-126">Serve como um wrapper lógico para a função Win32 correspondente, que recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="886a4-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="886a4-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="886a4-127">Remarks</span></span>  
 <span data-ttu-id="886a4-128">`IHostMemoryManager`também fornece métodos para o CLR obter um ponteiro por meio do qual fazer solicitações de memória no heap e obter o nível de pressão de memória no processo, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="886a4-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="886a4-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="886a4-129">Requirements</span></span>  
 <span data-ttu-id="886a4-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="886a4-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="886a4-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="886a4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="886a4-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="886a4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="886a4-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="886a4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886a4-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="886a4-134">See also</span></span>

- [<span data-ttu-id="886a4-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="886a4-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="886a4-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="886a4-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
