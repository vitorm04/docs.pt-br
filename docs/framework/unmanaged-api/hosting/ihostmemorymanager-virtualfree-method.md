---
title: "Método IHostMemoryManager::VirtualFree"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualFree
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 663c01d7e4b551ecf18bdd85a63aefc43f9750e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="b35bf-102">Método IHostMemoryManager::VirtualFree</span><span class="sxs-lookup"><span data-stu-id="b35bf-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="b35bf-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="b35bf-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="b35bf-104">A implementação do Win32 de `VirtualFree` libera, decommits, ou libera e decommits uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="b35bf-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b35bf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b35bf-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b35bf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b35bf-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="b35bf-107">[in] Um ponteiro para o endereço base das páginas de memória virtual para ser liberado.</span><span class="sxs-lookup"><span data-stu-id="b35bf-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="b35bf-108">[in] O tamanho, em bytes, da região para ser liberado.</span><span class="sxs-lookup"><span data-stu-id="b35bf-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="b35bf-109">[in] O tipo de operação de liberação.</span><span class="sxs-lookup"><span data-stu-id="b35bf-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b35bf-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b35bf-110">Return Value</span></span>  
  
|<span data-ttu-id="b35bf-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b35bf-111">HRESULT</span></span>|<span data-ttu-id="b35bf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b35bf-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b35bf-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b35bf-113">S_OK</span></span>|<span data-ttu-id="b35bf-114">`VirtualFree`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b35bf-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="b35bf-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b35bf-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b35bf-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b35bf-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b35bf-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b35bf-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b35bf-118">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b35bf-118">The call timed out.</span></span>|  
|<span data-ttu-id="b35bf-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b35bf-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b35bf-120">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b35bf-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b35bf-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b35bf-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b35bf-122">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b35bf-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b35bf-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b35bf-123">E_FAIL</span></span>|<span data-ttu-id="b35bf-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b35bf-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b35bf-125">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b35bf-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b35bf-126">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b35bf-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b35bf-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b35bf-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b35bf-128">Foi feita uma tentativa para liberar a memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="b35bf-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b35bf-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="b35bf-129">Remarks</span></span>  
 <span data-ttu-id="b35bf-130">`VirtualFree`libera páginas de memória virtual associadas a `lpAddress` parâmetro por meio de uma chamada anterior para o [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) função.</span><span class="sxs-lookup"><span data-stu-id="b35bf-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="b35bf-131">Tentativas para liberar a memória que não foi alocada por meio do host devem retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="b35bf-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="b35bf-132">A semântica é idêntica da implementação do Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="b35bf-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="b35bf-133">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="b35bf-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b35bf-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b35bf-134">Requirements</span></span>  
 <span data-ttu-id="b35bf-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b35bf-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b35bf-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b35bf-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b35bf-137">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b35bf-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b35bf-138">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b35bf-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b35bf-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b35bf-139">See Also</span></span>  
 [<span data-ttu-id="b35bf-140">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="b35bf-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="b35bf-141">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="b35bf-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
