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
ms.openlocfilehash: 4d37b7d803509ebfa861b7502d419f868bd12e11
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804381"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="2a912-102">Método IHostMemoryManager::VirtualFree</span><span class="sxs-lookup"><span data-stu-id="2a912-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="2a912-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="2a912-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="2a912-104">A implementação do Win32 de `VirtualFree` liberações, desconfirma ou libera e desconfirma uma região de páginas dentro do espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="2a912-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a912-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a912-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a912-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a912-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="2a912-107">no Um ponteiro para o endereço base das páginas de memória virtual a serem liberadas.</span><span class="sxs-lookup"><span data-stu-id="2a912-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="2a912-108">no O tamanho, em bytes, da região a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="2a912-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="2a912-109">no O tipo de operação de liberação.</span><span class="sxs-lookup"><span data-stu-id="2a912-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a912-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2a912-110">Return Value</span></span>  
  
|<span data-ttu-id="2a912-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a912-111">HRESULT</span></span>|<span data-ttu-id="2a912-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a912-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a912-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a912-113">S_OK</span></span>|<span data-ttu-id="2a912-114">`VirtualFree`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2a912-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="2a912-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2a912-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2a912-116">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2a912-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2a912-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2a912-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2a912-118">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2a912-118">The call timed out.</span></span>|  
|<span data-ttu-id="2a912-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a912-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2a912-120">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2a912-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2a912-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2a912-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2a912-122">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="2a912-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2a912-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2a912-123">E_FAIL</span></span>|<span data-ttu-id="2a912-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2a912-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2a912-125">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="2a912-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2a912-126">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2a912-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2a912-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2a912-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2a912-128">Foi feita uma tentativa de liberar memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="2a912-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a912-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a912-129">Remarks</span></span>  
 <span data-ttu-id="2a912-130">`VirtualFree`Libera as páginas de memória virtual associadas ao `lpAddress` parâmetro por meio de uma chamada anterior à função [IHostMemoryManager:: VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2a912-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="2a912-131">As tentativas de liberar memória que não foi alocada por meio do host devem retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="2a912-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="2a912-132">As semânticas são idênticas às da implementação do Win32 do `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="2a912-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="2a912-133">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="2a912-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a912-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a912-134">Requirements</span></span>  
 <span data-ttu-id="2a912-135">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a912-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a912-136">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2a912-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a912-137">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2a912-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a912-138">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a912-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a912-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a912-139">See also</span></span>

- [<span data-ttu-id="2a912-140">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="2a912-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="2a912-141">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="2a912-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
