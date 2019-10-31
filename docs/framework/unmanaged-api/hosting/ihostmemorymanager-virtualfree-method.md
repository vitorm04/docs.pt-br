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
ms.openlocfilehash: b53c0bb38922ae8de048c131807eb32f97423d6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128584"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="9d7ec-102">Método IHostMemoryManager::VirtualFree</span><span class="sxs-lookup"><span data-stu-id="9d7ec-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="9d7ec-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="9d7ec-104">A implementação do Win32 de `VirtualFree` liberações, desconfirma ou libera e desconfirma uma região de páginas dentro do espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7ec-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d7ec-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d7ec-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d7ec-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="9d7ec-107">no Um ponteiro para o endereço base das páginas de memória virtual a serem liberadas.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="9d7ec-108">no O tamanho, em bytes, da região a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="9d7ec-109">no O tipo de operação de liberação.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d7ec-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9d7ec-110">Return Value</span></span>  
  
|<span data-ttu-id="9d7ec-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d7ec-111">HRESULT</span></span>|<span data-ttu-id="9d7ec-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d7ec-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d7ec-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d7ec-113">S_OK</span></span>|<span data-ttu-id="9d7ec-114">`VirtualFree` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="9d7ec-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d7ec-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d7ec-116">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d7ec-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d7ec-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d7ec-118">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-118">The call timed out.</span></span>|  
|<span data-ttu-id="9d7ec-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d7ec-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d7ec-120">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d7ec-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d7ec-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d7ec-122">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d7ec-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d7ec-123">E_FAIL</span></span>|<span data-ttu-id="9d7ec-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d7ec-125">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d7ec-126">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d7ec-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="9d7ec-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="9d7ec-128">Foi feita uma tentativa de liberar memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d7ec-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d7ec-129">Remarks</span></span>  
 <span data-ttu-id="9d7ec-130">`VirtualFree` libera as páginas de memória virtual associadas ao parâmetro `lpAddress` por meio de uma chamada anterior à função [IHostMemoryManager:: VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d7ec-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="9d7ec-131">As tentativas de liberar memória que não foi alocada por meio do host devem retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="9d7ec-132">A semântica é idêntica àquelas da implementação do Win32 do `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="9d7ec-133">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="9d7ec-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7ec-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d7ec-134">Requirements</span></span>  
 <span data-ttu-id="9d7ec-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d7ec-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d7ec-136">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d7ec-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d7ec-137">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d7ec-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d7ec-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d7ec-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7ec-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d7ec-139">See also</span></span>

- [<span data-ttu-id="9d7ec-140">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="9d7ec-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="9d7ec-141">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="9d7ec-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
