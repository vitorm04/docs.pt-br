---
title: Método IHostMemoryManager::VirtualFree
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03cac2b8433d6491d1fa474a0d4064ef4e260d6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993220"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="783ca-102">Método IHostMemoryManager::VirtualFree</span><span class="sxs-lookup"><span data-stu-id="783ca-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="783ca-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="783ca-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="783ca-104">A implementação do Win32 de `VirtualFree` versões, desfaz a confirmação, ou versões e anulações de confirmação de uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="783ca-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="783ca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="783ca-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="783ca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="783ca-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="783ca-107">[in] Um ponteiro para o endereço básico das páginas de memória virtual a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="783ca-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="783ca-108">[in] O tamanho, em bytes, da região a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="783ca-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="783ca-109">[in] O tipo de operação de liberação.</span><span class="sxs-lookup"><span data-stu-id="783ca-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="783ca-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="783ca-110">Return Value</span></span>  
  
|<span data-ttu-id="783ca-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="783ca-111">HRESULT</span></span>|<span data-ttu-id="783ca-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="783ca-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="783ca-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="783ca-113">S_OK</span></span>|<span data-ttu-id="783ca-114">`VirtualFree` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="783ca-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="783ca-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="783ca-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="783ca-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="783ca-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="783ca-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="783ca-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="783ca-118">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="783ca-118">The call timed out.</span></span>|  
|<span data-ttu-id="783ca-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="783ca-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="783ca-120">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="783ca-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="783ca-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="783ca-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="783ca-122">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="783ca-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="783ca-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="783ca-123">E_FAIL</span></span>|<span data-ttu-id="783ca-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="783ca-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="783ca-125">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="783ca-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="783ca-126">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="783ca-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="783ca-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="783ca-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="783ca-128">Foi feita uma tentativa para liberar a memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="783ca-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="783ca-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="783ca-129">Remarks</span></span>  
 <span data-ttu-id="783ca-130">`VirtualFree` libera a memória virtual páginas associadas com o `lpAddress` parâmetro por meio de uma chamada anterior para o [ihostmemorymanager:: VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) função.</span><span class="sxs-lookup"><span data-stu-id="783ca-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="783ca-131">Tenta liberar a memória que não foi alocada por meio do host deve retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="783ca-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="783ca-132">A semântica é idêntica da implementação do Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="783ca-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="783ca-133">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="783ca-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="783ca-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="783ca-134">Requirements</span></span>  
 <span data-ttu-id="783ca-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="783ca-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="783ca-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="783ca-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="783ca-137">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="783ca-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="783ca-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="783ca-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="783ca-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="783ca-139">See also</span></span>

- [<span data-ttu-id="783ca-140">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="783ca-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="783ca-141">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="783ca-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
