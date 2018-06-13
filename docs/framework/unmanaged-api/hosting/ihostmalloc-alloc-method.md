---
title: Método IHostMAlloc::Alloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d67704aae80113bd41df5ea38acf2a794aacbac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439040"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="1dac7-102">Método IHostMAlloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="1dac7-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="1dac7-103">Solicita que o host alocar a quantidade especificada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="1dac7-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dac7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1dac7-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dac7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1dac7-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="1dac7-106">[in] O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="1dac7-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="1dac7-107">[in] Uma da [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valores, que indica o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="1dac7-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="1dac7-108">[out] Um ponteiro para a memória alocada, ou nulo se a solicitação não pôde ser concluída.</span><span class="sxs-lookup"><span data-stu-id="1dac7-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dac7-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1dac7-109">Return Value</span></span>  
  
|<span data-ttu-id="1dac7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dac7-110">HRESULT</span></span>|<span data-ttu-id="1dac7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dac7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dac7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dac7-112">S_OK</span></span>|<span data-ttu-id="1dac7-113">`Alloc` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="1dac7-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="1dac7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1dac7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1dac7-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1dac7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1dac7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1dac7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1dac7-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="1dac7-117">The call timed out.</span></span>|  
|<span data-ttu-id="1dac7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1dac7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1dac7-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1dac7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1dac7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1dac7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1dac7-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="1dac7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1dac7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1dac7-122">E_FAIL</span></span>|<span data-ttu-id="1dac7-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1dac7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1dac7-124">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1dac7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1dac7-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1dac7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1dac7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1dac7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1dac7-127">Não havia memória suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="1dac7-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dac7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="1dac7-128">Remarks</span></span>  
 <span data-ttu-id="1dac7-129">O CLR obtém um ponteiro de interface para um `IHostMalloc` instância chamando o [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1dac7-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dac7-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1dac7-130">Requirements</span></span>  
 <span data-ttu-id="1dac7-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dac7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dac7-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1dac7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dac7-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1dac7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dac7-134">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dac7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dac7-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dac7-135">See Also</span></span>  
 [<span data-ttu-id="1dac7-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="1dac7-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="1dac7-137">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="1dac7-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
