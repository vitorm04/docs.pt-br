---
title: Método IHostSemaphore::ReleaseSemaphore
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e977133d722edc7d090d07cd117ee282a8d29cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753573"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="1cee0-102">Método IHostSemaphore::ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="1cee0-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="1cee0-103">Aumenta a contagem do atual [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instância pelo valor especificado.</span><span class="sxs-lookup"><span data-stu-id="1cee0-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cee0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cee0-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cee0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cee0-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="1cee0-106">[in] O valor pelo qual incrementar a contagem atual `IHostSemaphore` instância.</span><span class="sxs-lookup"><span data-stu-id="1cee0-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="1cee0-107">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="1cee0-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="1cee0-108">[out] Um ponteiro para a contagem anterior, ou nulo se o chamador não exigir a contagem anterior.</span><span class="sxs-lookup"><span data-stu-id="1cee0-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cee0-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1cee0-109">Return Value</span></span>  
  
|<span data-ttu-id="1cee0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1cee0-110">HRESULT</span></span>|<span data-ttu-id="1cee0-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cee0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1cee0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1cee0-112">S_OK</span></span>|<span data-ttu-id="1cee0-113">`ReleaseSemaphore` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1cee0-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="1cee0-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1cee0-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1cee0-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1cee0-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1cee0-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1cee0-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1cee0-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1cee0-117">The call timed out.</span></span>|  
|<span data-ttu-id="1cee0-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1cee0-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1cee0-119">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1cee0-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1cee0-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1cee0-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1cee0-121">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="1cee0-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1cee0-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1cee0-122">E_FAIL</span></span>|<span data-ttu-id="1cee0-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1cee0-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1cee0-124">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1cee0-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1cee0-125">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1cee0-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cee0-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cee0-126">Remarks</span></span>  
 <span data-ttu-id="1cee0-127">O CLR chama normalmente `ReleaseSemaphore` para notificar o host que ele tiver terminado de usar um recurso, passando um valor de 1 para o `lReleaseCount` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1cee0-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cee0-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cee0-128">Requirements</span></span>  
 <span data-ttu-id="1cee0-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cee0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cee0-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1cee0-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1cee0-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1cee0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cee0-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cee0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cee0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cee0-133">See also</span></span>

- [<span data-ttu-id="1cee0-134">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="1cee0-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="1cee0-135">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="1cee0-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="1cee0-136">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="1cee0-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="1cee0-137">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="1cee0-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="1cee0-138">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="1cee0-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
