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
ms.openlocfilehash: 622b6c523adfb7bae2fc38826152ef69709568cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931070"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="39a1e-102">Método IHostSyncManager::CreateCrst</span><span class="sxs-lookup"><span data-stu-id="39a1e-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="39a1e-103">Cria um objeto de seção crítica para sincronização.</span><span class="sxs-lookup"><span data-stu-id="39a1e-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39a1e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39a1e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39a1e-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="39a1e-106">fora Um ponteiro para o endereço de uma instância de [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) implementada pelo host, ou NULL se a seção crítica não puder ser criada.</span><span class="sxs-lookup"><span data-stu-id="39a1e-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39a1e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="39a1e-107">Return Value</span></span>  
  
|<span data-ttu-id="39a1e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39a1e-108">HRESULT</span></span>|<span data-ttu-id="39a1e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="39a1e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39a1e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="39a1e-110">S_OK</span></span>|<span data-ttu-id="39a1e-111">`CreateCrst`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="39a1e-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="39a1e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="39a1e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="39a1e-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="39a1e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="39a1e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="39a1e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="39a1e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="39a1e-115">The call timed out.</span></span>|  
|<span data-ttu-id="39a1e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="39a1e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="39a1e-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="39a1e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="39a1e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="39a1e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="39a1e-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="39a1e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="39a1e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="39a1e-120">E_FAIL</span></span>|<span data-ttu-id="39a1e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="39a1e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="39a1e-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="39a1e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="39a1e-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="39a1e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="39a1e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="39a1e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="39a1e-125">Não há memória suficiente disponível para criar a seção crítica solicitada.</span><span class="sxs-lookup"><span data-stu-id="39a1e-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39a1e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="39a1e-126">Remarks</span></span>  
 <span data-ttu-id="39a1e-127">Os objetos de seção crítica fornecem sincronização semelhante à fornecida por um objeto mutex, exceto que as seções críticas podem ser usadas somente pelos threads de um único processo.</span><span class="sxs-lookup"><span data-stu-id="39a1e-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="39a1e-128">`CreateCrst`espelha a função `InitializeCriticalSection` do Win32.</span><span class="sxs-lookup"><span data-stu-id="39a1e-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39a1e-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39a1e-129">Requirements</span></span>  
 <span data-ttu-id="39a1e-130">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39a1e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39a1e-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="39a1e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39a1e-132">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="39a1e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39a1e-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39a1e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a1e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39a1e-134">See also</span></span>

- [<span data-ttu-id="39a1e-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="39a1e-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="39a1e-136">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="39a1e-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="39a1e-137">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="39a1e-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="39a1e-138">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="39a1e-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="39a1e-139">Mutexes</span><span class="sxs-lookup"><span data-stu-id="39a1e-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="39a1e-140">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="39a1e-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
