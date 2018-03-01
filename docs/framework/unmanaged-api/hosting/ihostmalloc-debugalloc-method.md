---
title: "Método IHostMAlloc::DebugAlloc"
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
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63249f6ce64071ddaa2bb9dff221ae40d924bbfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="debc6-102">Método IHostMAlloc::DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="debc6-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="debc6-103">Solicita que o host alocar a quantidade especificada de memória de heap e Além disso, controlar em que a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="debc6-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="debc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="debc6-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="debc6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="debc6-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="debc6-106">[in] O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="debc6-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="debc6-107">[in] Uma da [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valores, que indica o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="debc6-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="debc6-108">[in] O arquivo de código do executável que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="debc6-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="debc6-109">[in] O número da linha em `pszFileName` onde a alocação foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="debc6-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="debc6-110">[out] Um ponteiro para a memória alocada, ou nulo se a solicitação não pôde ser concluída.</span><span class="sxs-lookup"><span data-stu-id="debc6-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="debc6-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="debc6-111">Return Value</span></span>  
  
|<span data-ttu-id="debc6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="debc6-112">HRESULT</span></span>|<span data-ttu-id="debc6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="debc6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="debc6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="debc6-114">S_OK</span></span>|<span data-ttu-id="debc6-115">`DebugAlloc`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="debc6-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="debc6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="debc6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="debc6-117">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="debc6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="debc6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="debc6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="debc6-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="debc6-119">The call timed out.</span></span>|  
|<span data-ttu-id="debc6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="debc6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="debc6-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="debc6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="debc6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="debc6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="debc6-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="debc6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="debc6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="debc6-124">E_FAIL</span></span>|<span data-ttu-id="debc6-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="debc6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="debc6-126">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="debc6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="debc6-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="debc6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="debc6-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="debc6-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="debc6-129">Não havia memória suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="debc6-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="debc6-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="debc6-130">Remarks</span></span>  
 <span data-ttu-id="debc6-131">O CLR obtém um ponteiro de interface para um [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instância chamando o [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="debc6-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="debc6-132">`DebugAlloc`permite que o tempo de execução obter informações do arquivo de código para uso durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="debc6-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="debc6-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="debc6-133">Requirements</span></span>  
 <span data-ttu-id="debc6-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="debc6-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="debc6-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="debc6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="debc6-136">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="debc6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="debc6-137">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="debc6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="debc6-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="debc6-138">See Also</span></span>  
 [<span data-ttu-id="debc6-139">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="debc6-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="debc6-140">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="debc6-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
