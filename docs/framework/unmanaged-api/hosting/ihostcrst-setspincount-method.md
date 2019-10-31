---
title: Método IHostCrst::SetSpinCount
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: a8642235cda359b849c49a35ab565397402c37d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130508"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="bcdc7-102">Método IHostCrst::SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="bcdc7-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="bcdc7-103">Define a contagem de rotação para a instância de [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcdc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcdc7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcdc7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bcdc7-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="bcdc7-106">no A nova contagem de rotação para a instância de `IHostCrst` atual.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bcdc7-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bcdc7-107">Return Value</span></span>  
  
|<span data-ttu-id="bcdc7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bcdc7-108">HRESULT</span></span>|<span data-ttu-id="bcdc7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcdc7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bcdc7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bcdc7-110">S_OK</span></span>|<span data-ttu-id="bcdc7-111">`SetSpinCount` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="bcdc7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bcdc7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bcdc7-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bcdc7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bcdc7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bcdc7-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-115">The call timed out.</span></span>|  
|<span data-ttu-id="bcdc7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bcdc7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bcdc7-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bcdc7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bcdc7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bcdc7-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bcdc7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bcdc7-120">E_FAIL</span></span>|<span data-ttu-id="bcdc7-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bcdc7-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bcdc7-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcdc7-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="bcdc7-124">Remarks</span></span>  
 <span data-ttu-id="bcdc7-125">Em sistemas com vários processadores, se a seção crítica representada pela instância de `IHostCrst` atual não estiver disponível, um thread de chamada será girado `dwSpinCount` vezes antes de chamar [IHostSemaphore:: Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) em um semáforo associado à seção crítica.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="bcdc7-126">Se a seção crítica for liberada durante a operação de rotação, o thread de chamada evitará a operação de espera.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="bcdc7-127">O uso de `dwSpinCount` é idêntico ao uso do parâmetro do mesmo nome na função de `InitializeCriticalSectionAndSpinCount` do Win32.</span><span class="sxs-lookup"><span data-stu-id="bcdc7-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcdc7-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bcdc7-128">Requirements</span></span>  
 <span data-ttu-id="bcdc7-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcdc7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcdc7-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bcdc7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcdc7-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bcdc7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcdc7-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcdc7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcdc7-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcdc7-133">See also</span></span>

- [<span data-ttu-id="bcdc7-134">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="bcdc7-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="bcdc7-135">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="bcdc7-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="bcdc7-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="bcdc7-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
