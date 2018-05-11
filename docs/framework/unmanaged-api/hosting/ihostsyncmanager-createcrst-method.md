---
title: Método IHostSyncManager::CreateCrst
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101a652aa77e587003fb7e773e00ba9b77461a06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="79cf9-102">Método IHostSyncManager::CreateCrst</span><span class="sxs-lookup"><span data-stu-id="79cf9-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="79cf9-103">Cria um objeto de seção crítica para sincronização.</span><span class="sxs-lookup"><span data-stu-id="79cf9-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79cf9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79cf9-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79cf9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79cf9-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="79cf9-106">[out] Um ponteiro para o endereço de um [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instância implementada pelo host, ou nula se não foi possível criar a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="79cf9-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79cf9-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="79cf9-107">Return Value</span></span>  
  
|<span data-ttu-id="79cf9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79cf9-108">HRESULT</span></span>|<span data-ttu-id="79cf9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="79cf9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79cf9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="79cf9-110">S_OK</span></span>|<span data-ttu-id="79cf9-111">`CreateCrst` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="79cf9-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="79cf9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79cf9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79cf9-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="79cf9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79cf9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79cf9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79cf9-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="79cf9-115">The call timed out.</span></span>|  
|<span data-ttu-id="79cf9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79cf9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79cf9-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="79cf9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79cf9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79cf9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79cf9-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="79cf9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79cf9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79cf9-120">E_FAIL</span></span>|<span data-ttu-id="79cf9-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="79cf9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79cf9-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="79cf9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79cf9-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="79cf9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="79cf9-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="79cf9-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="79cf9-125">Não havia memória suficiente disponível para criar a seção crítica solicitada.</span><span class="sxs-lookup"><span data-stu-id="79cf9-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79cf9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="79cf9-126">Remarks</span></span>  
 <span data-ttu-id="79cf9-127">Objetos de seção crítica fornecem sincronização semelhante àquela fornecida por um objeto mutex, exceto que as seções críticas podem ser usadas somente por segmentos de um único processo.</span><span class="sxs-lookup"><span data-stu-id="79cf9-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="79cf9-128">`CreateCrst` reflete o Win32 `InitializeCriticalSection` função.</span><span class="sxs-lookup"><span data-stu-id="79cf9-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79cf9-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79cf9-129">Requirements</span></span>  
 <span data-ttu-id="79cf9-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79cf9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79cf9-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79cf9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79cf9-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="79cf9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79cf9-133">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79cf9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79cf9-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79cf9-134">See Also</span></span>  
 [<span data-ttu-id="79cf9-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="79cf9-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="79cf9-136">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="79cf9-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="79cf9-137">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="79cf9-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="79cf9-138">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="79cf9-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="79cf9-139">Mutexes</span><span class="sxs-lookup"><span data-stu-id="79cf9-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="79cf9-140">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="79cf9-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
