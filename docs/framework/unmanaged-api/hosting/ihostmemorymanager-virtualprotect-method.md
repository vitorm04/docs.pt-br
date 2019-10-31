---
title: Método IHostMemoryManager::VirtualProtect
ms.date: 03/30/2017
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
ms.openlocfilehash: d39ad45e143026f40ffcf1339e923837f9e812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195855"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="e8ed8-102">Método IHostMemoryManager::VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="e8ed8-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="e8ed8-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="e8ed8-104">A implementação do Win32 de `VirtualProtect` altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ed8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8ed8-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8ed8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8ed8-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="e8ed8-107">no Um ponteiro para o endereço base da memória virtual cujos atributos de proteção devem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="e8ed8-108">no O tamanho, em bytes, da região das páginas de memória a ser alterada.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="e8ed8-109">no O tipo de proteção de memória a ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="e8ed8-110">fora Um ponteiro para o valor de proteção de memória anterior.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8ed8-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e8ed8-111">Return Value</span></span>  
  
|<span data-ttu-id="e8ed8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8ed8-112">HRESULT</span></span>|<span data-ttu-id="e8ed8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8ed8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8ed8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8ed8-114">S_OK</span></span>|<span data-ttu-id="e8ed8-115">`VirtualProtect` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="e8ed8-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8ed8-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8ed8-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8ed8-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8ed8-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8ed8-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-119">The call timed out.</span></span>|  
|<span data-ttu-id="e8ed8-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8ed8-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8ed8-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8ed8-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8ed8-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8ed8-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8ed8-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8ed8-124">E_FAIL</span></span>|<span data-ttu-id="e8ed8-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8ed8-126">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8ed8-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8ed8-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8ed8-128">Remarks</span></span>  
 <span data-ttu-id="e8ed8-129">Essa implementação de `VirtualProtect` retorna um valor HRESULT, enquanto a implementação do Win32 retorna um valor diferente de zero para indicar êxito e um valor zero para indicar falha.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="e8ed8-130">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="e8ed8-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ed8-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8ed8-131">Requirements</span></span>  
 <span data-ttu-id="e8ed8-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ed8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ed8-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8ed8-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8ed8-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e8ed8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8ed8-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ed8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ed8-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8ed8-136">See also</span></span>

- [<span data-ttu-id="e8ed8-137">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="e8ed8-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
