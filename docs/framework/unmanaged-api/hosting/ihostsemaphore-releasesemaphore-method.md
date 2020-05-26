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
ms.openlocfilehash: aa67aabbe8a7a47a9b3036f508e2f8bb6082c3e0
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803550"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="17cbf-102">Método IHostSemaphore::ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="17cbf-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="17cbf-103">Aumenta a contagem da instância de [IHostSemaphore](ihostsemaphore-interface.md) atual pelo valor especificado.</span><span class="sxs-lookup"><span data-stu-id="17cbf-103">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17cbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17cbf-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17cbf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17cbf-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="17cbf-106">no O valor pelo qual aumentar a contagem da `IHostSemaphore` instância atual.</span><span class="sxs-lookup"><span data-stu-id="17cbf-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="17cbf-107">Essa quantidade deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="17cbf-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="17cbf-108">fora Um ponteiro para a contagem anterior ou NULL se o chamador não exigir a contagem anterior.</span><span class="sxs-lookup"><span data-stu-id="17cbf-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17cbf-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="17cbf-109">Return Value</span></span>  
  
|<span data-ttu-id="17cbf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17cbf-110">HRESULT</span></span>|<span data-ttu-id="17cbf-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="17cbf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17cbf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="17cbf-112">S_OK</span></span>|<span data-ttu-id="17cbf-113">`ReleaseSemaphore`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="17cbf-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="17cbf-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17cbf-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17cbf-115">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="17cbf-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17cbf-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17cbf-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17cbf-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="17cbf-117">The call timed out.</span></span>|  
|<span data-ttu-id="17cbf-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17cbf-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17cbf-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="17cbf-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17cbf-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17cbf-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17cbf-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="17cbf-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17cbf-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17cbf-122">E_FAIL</span></span>|<span data-ttu-id="17cbf-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="17cbf-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17cbf-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="17cbf-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17cbf-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="17cbf-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17cbf-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="17cbf-126">Remarks</span></span>  
 <span data-ttu-id="17cbf-127">O CLR normalmente chama `ReleaseSemaphore` para notificar o host de que ele concluiu o uso de um recurso, passando um valor de 1 para o `lReleaseCount` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="17cbf-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17cbf-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17cbf-128">Requirements</span></span>  
 <span data-ttu-id="17cbf-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17cbf-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cbf-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17cbf-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17cbf-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17cbf-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17cbf-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cbf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cbf-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="17cbf-133">See also</span></span>

- [<span data-ttu-id="17cbf-134">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="17cbf-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="17cbf-135">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="17cbf-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="17cbf-136">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="17cbf-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="17cbf-137">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="17cbf-137">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="17cbf-138">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="17cbf-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
