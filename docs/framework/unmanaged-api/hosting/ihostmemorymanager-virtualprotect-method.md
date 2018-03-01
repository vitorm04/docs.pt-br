---
title: "Método IHostMemoryManager::VirtualProtect"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77e8e163a16752934d0a1d826cc8463b3d3281bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="3a982-102">Método IHostMemoryManager::VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="3a982-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="3a982-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="3a982-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="3a982-104">A implementação do Win32 de `VirtualProtect` altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="3a982-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a982-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a982-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a982-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a982-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="3a982-107">[in] Um ponteiro para o endereço base da memória virtual cujos atributos de proteção devem ser alteradas.</span><span class="sxs-lookup"><span data-stu-id="3a982-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="3a982-108">[in] O tamanho, em bytes, da região de páginas de memória a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="3a982-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="3a982-109">[in] O tipo de proteção de memória para aplicar.</span><span class="sxs-lookup"><span data-stu-id="3a982-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="3a982-110">[out] Um ponteiro para o valor anterior de proteção de memória.</span><span class="sxs-lookup"><span data-stu-id="3a982-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a982-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3a982-111">Return Value</span></span>  
  
|<span data-ttu-id="3a982-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a982-112">HRESULT</span></span>|<span data-ttu-id="3a982-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a982-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a982-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a982-114">S_OK</span></span>|<span data-ttu-id="3a982-115">`VirtualProtect`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="3a982-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="3a982-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a982-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a982-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3a982-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a982-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a982-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a982-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="3a982-119">The call timed out.</span></span>|  
|<span data-ttu-id="3a982-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a982-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a982-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3a982-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a982-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a982-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a982-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="3a982-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a982-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a982-124">E_FAIL</span></span>|<span data-ttu-id="3a982-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3a982-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a982-126">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3a982-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a982-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3a982-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a982-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a982-128">Remarks</span></span>  
 <span data-ttu-id="3a982-129">Essa implementação de `VirtualProtect` retorna um valor HRESULT, enquanto a implementação de Win32 retorna um valor diferente de zero para indicar êxito e um valor igual a zero para indicar falha.</span><span class="sxs-lookup"><span data-stu-id="3a982-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="3a982-130">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="3a982-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a982-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a982-131">Requirements</span></span>  
 <span data-ttu-id="3a982-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a982-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a982-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a982-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a982-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3a982-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a982-135">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a982-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a982-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a982-136">See Also</span></span>  
 [<span data-ttu-id="3a982-137">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="3a982-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
