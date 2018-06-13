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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d90bce1f693f571a5d5c5d5dca981d09bce59b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438841"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="150fc-102">Método IHostCrst::SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="150fc-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="150fc-103">Define a contagem de rotação atual [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="150fc-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="150fc-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="150fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="150fc-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="150fc-106">[in] A nova contagem de rotação atual `IHostCrst` instância.</span><span class="sxs-lookup"><span data-stu-id="150fc-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="150fc-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="150fc-107">Return Value</span></span>  
  
|<span data-ttu-id="150fc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="150fc-108">HRESULT</span></span>|<span data-ttu-id="150fc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="150fc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="150fc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="150fc-110">S_OK</span></span>|<span data-ttu-id="150fc-111">`SetSpinCount` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="150fc-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="150fc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="150fc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="150fc-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="150fc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="150fc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="150fc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="150fc-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="150fc-115">The call timed out.</span></span>|  
|<span data-ttu-id="150fc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="150fc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="150fc-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="150fc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="150fc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="150fc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="150fc-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="150fc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="150fc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="150fc-120">E_FAIL</span></span>|<span data-ttu-id="150fc-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="150fc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="150fc-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="150fc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="150fc-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="150fc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="150fc-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="150fc-124">Remarks</span></span>  
 <span data-ttu-id="150fc-125">Em sistemas com vários processadores, se a seção crítica representados por atual `IHostCrst` instância não está disponível, um thread de chamada gira `dwSpinCount` vezes antes de chamar [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) em um semáforo associado com a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="150fc-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="150fc-126">Se a seção crítica ficar livre durante a operação de rotação, o thread de chamada evita a operação de espera.</span><span class="sxs-lookup"><span data-stu-id="150fc-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="150fc-127">O uso de `dwSpinCount` é idêntica ao uso do parâmetro do mesmo nome em Win32 `InitializeCriticalSectionAndSpinCount` função.</span><span class="sxs-lookup"><span data-stu-id="150fc-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="150fc-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="150fc-128">Requirements</span></span>  
 <span data-ttu-id="150fc-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="150fc-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="150fc-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="150fc-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="150fc-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="150fc-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="150fc-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="150fc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="150fc-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="150fc-133">See Also</span></span>  
 [<span data-ttu-id="150fc-134">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="150fc-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="150fc-135">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="150fc-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="150fc-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="150fc-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
