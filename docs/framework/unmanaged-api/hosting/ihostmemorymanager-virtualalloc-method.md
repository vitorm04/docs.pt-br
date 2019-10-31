---
title: Método IHostMemoryManager::VirtualAlloc
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: dd588fa85ff8aaa396a8d0e52a738ada46c2a9b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128609"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="27084-102">Método IHostMemoryManager::VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="27084-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="27084-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="27084-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="27084-104">A implementação do Win32 de `VirtualAlloc` reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="27084-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27084-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27084-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27084-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27084-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="27084-107">no Um ponteiro para o endereço inicial da região a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="27084-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="27084-108">no O tamanho, em bytes, da região.</span><span class="sxs-lookup"><span data-stu-id="27084-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="27084-109">no O tipo de alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="27084-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="27084-110">no Proteção de memória para a região de páginas a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="27084-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="27084-111">no Um valor de [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) que indica o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="27084-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="27084-112">fora Ponteiro para o endereço inicial da memória alocada, ou NULL se a solicitação não puder ser atendida.</span><span class="sxs-lookup"><span data-stu-id="27084-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27084-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="27084-113">Return Value</span></span>  
  
|<span data-ttu-id="27084-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27084-114">HRESULT</span></span>|<span data-ttu-id="27084-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="27084-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27084-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="27084-116">S_OK</span></span>|<span data-ttu-id="27084-117">`VirtualAlloc` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="27084-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="27084-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="27084-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="27084-119">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="27084-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="27084-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="27084-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="27084-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="27084-121">The call timed out.</span></span>|  
|<span data-ttu-id="27084-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="27084-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="27084-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="27084-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="27084-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="27084-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="27084-125">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="27084-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="27084-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27084-126">E_FAIL</span></span>|<span data-ttu-id="27084-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="27084-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="27084-128">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="27084-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="27084-129">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="27084-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="27084-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="27084-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="27084-131">Não havia memória suficiente disponível para concluir a solicitação de alocação</span><span class="sxs-lookup"><span data-stu-id="27084-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27084-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="27084-132">Remarks</span></span>  
 <span data-ttu-id="27084-133">Você reserva uma região no espaço de endereço do processo chamando `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="27084-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="27084-134">O parâmetro `pAddress` contém o endereço inicial do bloco de memória que você deseja.</span><span class="sxs-lookup"><span data-stu-id="27084-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="27084-135">Esse parâmetro é normalmente definido como nulo.</span><span class="sxs-lookup"><span data-stu-id="27084-135">This parameter is typically set to null.</span></span> <span data-ttu-id="27084-136">O sistema operacional mantém um registro de intervalos de endereços livres disponíveis para seu processo.</span><span class="sxs-lookup"><span data-stu-id="27084-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="27084-137">Um valor `pAddress` de NULL instrui o sistema a reservar a região onde quer que ela se ajuste.</span><span class="sxs-lookup"><span data-stu-id="27084-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="27084-138">Como alternativa, você pode fornecer um endereço inicial específico para o bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="27084-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="27084-139">Em ambos os casos, o parâmetro de saída `ppMem` é retornado como um ponteiro para a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="27084-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="27084-140">A função em si retorna um valor HRESULT.</span><span class="sxs-lookup"><span data-stu-id="27084-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="27084-141">A função de `VirtualAlloc` do Win32 não tem um parâmetro `ppMem` e retorna o ponteiro para a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="27084-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="27084-142">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="27084-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27084-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27084-143">Requirements</span></span>  
 <span data-ttu-id="27084-144">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27084-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27084-145">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="27084-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27084-146">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27084-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27084-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27084-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27084-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27084-148">See also</span></span>

- [<span data-ttu-id="27084-149">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="27084-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
