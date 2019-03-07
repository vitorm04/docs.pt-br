---
title: Método IHostSemaphore::Wait
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9933948a5e67b91106cdadc6f747c1b1c4121813
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489989"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="97f8b-102">Método IHostSemaphore::Wait</span><span class="sxs-lookup"><span data-stu-id="97f8b-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="97f8b-103">Faz com que o atual [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instância aguardar até que ele pertence ou a quantidade especificada de tempo passa.</span><span class="sxs-lookup"><span data-stu-id="97f8b-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97f8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97f8b-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97f8b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97f8b-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="97f8b-106">[in] O número de milissegundos de espera antes de retornar, se o atual `IHostSemaphore` instância não é de propriedade.</span><span class="sxs-lookup"><span data-stu-id="97f8b-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="97f8b-107">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores, especificando qual ação o host deve executar se este blocos de operação.</span><span class="sxs-lookup"><span data-stu-id="97f8b-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97f8b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="97f8b-108">Return Value</span></span>  
  
|<span data-ttu-id="97f8b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97f8b-109">HRESULT</span></span>|<span data-ttu-id="97f8b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="97f8b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97f8b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="97f8b-111">S_OK</span></span>|<span data-ttu-id="97f8b-112">`Wait` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="97f8b-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="97f8b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97f8b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97f8b-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="97f8b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97f8b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97f8b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97f8b-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="97f8b-116">The call timed out.</span></span>|  
|<span data-ttu-id="97f8b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97f8b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97f8b-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="97f8b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97f8b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97f8b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97f8b-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="97f8b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97f8b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97f8b-121">E_FAIL</span></span>|<span data-ttu-id="97f8b-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="97f8b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97f8b-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="97f8b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97f8b-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97f8b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="97f8b-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="97f8b-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="97f8b-126">O host detectou um deadlock durante o intervalo de espera e escolheu atual `IHostSemaphore` instância como uma vítima de deadlock.</span><span class="sxs-lookup"><span data-stu-id="97f8b-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97f8b-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97f8b-127">Requirements</span></span>  
 <span data-ttu-id="97f8b-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97f8b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97f8b-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97f8b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97f8b-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="97f8b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97f8b-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97f8b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f8b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97f8b-132">See also</span></span>
- [<span data-ttu-id="97f8b-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="97f8b-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="97f8b-134">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="97f8b-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="97f8b-135">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="97f8b-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="97f8b-136">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="97f8b-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="97f8b-137">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="97f8b-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
