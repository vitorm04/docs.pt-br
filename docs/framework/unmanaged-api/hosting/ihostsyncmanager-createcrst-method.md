---
title: "Método IHostSyncManager::CreateCrst"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b54abb60b00d071900d3bfdd01c2e5f1807998a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="bac1b-102">Método IHostSyncManager::CreateCrst</span><span class="sxs-lookup"><span data-stu-id="bac1b-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="bac1b-103">Cria um objeto de seção crítica para sincronização.</span><span class="sxs-lookup"><span data-stu-id="bac1b-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac1b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bac1b-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bac1b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bac1b-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="bac1b-106">[out] Um ponteiro para o endereço de um [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instância implementada pelo host, ou nula se não foi possível criar a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="bac1b-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bac1b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bac1b-107">Return Value</span></span>  
  
|<span data-ttu-id="bac1b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bac1b-108">HRESULT</span></span>|<span data-ttu-id="bac1b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bac1b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bac1b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bac1b-110">S_OK</span></span>|<span data-ttu-id="bac1b-111">`CreateCrst`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="bac1b-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="bac1b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bac1b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bac1b-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bac1b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bac1b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bac1b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bac1b-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="bac1b-115">The call timed out.</span></span>|  
|<span data-ttu-id="bac1b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bac1b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bac1b-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bac1b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bac1b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bac1b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bac1b-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="bac1b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bac1b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bac1b-120">E_FAIL</span></span>|<span data-ttu-id="bac1b-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bac1b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bac1b-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bac1b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bac1b-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bac1b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bac1b-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bac1b-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bac1b-125">Não havia memória suficiente disponível para criar a seção crítica solicitada.</span><span class="sxs-lookup"><span data-stu-id="bac1b-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bac1b-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="bac1b-126">Remarks</span></span>  
 <span data-ttu-id="bac1b-127">Objetos de seção crítica fornecem sincronização semelhante àquela fornecida por um objeto mutex, exceto que as seções críticas podem ser usadas somente por segmentos de um único processo.</span><span class="sxs-lookup"><span data-stu-id="bac1b-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="bac1b-128">`CreateCrst`reflete o Win32 `InitializeCriticalSection` função.</span><span class="sxs-lookup"><span data-stu-id="bac1b-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac1b-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bac1b-129">Requirements</span></span>  
 <span data-ttu-id="bac1b-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac1b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac1b-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bac1b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bac1b-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bac1b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bac1b-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac1b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac1b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bac1b-134">See Also</span></span>  
 [<span data-ttu-id="bac1b-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="bac1b-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="bac1b-136">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="bac1b-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="bac1b-137">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="bac1b-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="bac1b-138">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="bac1b-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="bac1b-139">Mutexes</span><span class="sxs-lookup"><span data-stu-id="bac1b-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="bac1b-140">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="bac1b-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
