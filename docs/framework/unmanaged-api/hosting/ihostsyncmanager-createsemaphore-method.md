---
title: Método IHostSyncManager::CreateSemaphore
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 003e385ade6357b76823986d20e8fdf3d4c3757f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446138"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="e41f7-102">Método IHostSyncManager::CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="e41f7-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="e41f7-103">Cria um [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objeto para o common language runtime (CLR) para usar como um sinal para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="e41f7-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e41f7-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e41f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e41f7-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="e41f7-106">[in] A contagem inicial de `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="e41f7-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="e41f7-107">[in] A contagem máxima de `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="e41f7-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="e41f7-108">[out] Um ponteiro para o endereço de um `IHostSemaphore` de instância, ou nulo se o sinal não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="e41f7-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e41f7-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e41f7-109">Return Value</span></span>  
  
|<span data-ttu-id="e41f7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e41f7-110">HRESULT</span></span>|<span data-ttu-id="e41f7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e41f7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e41f7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e41f7-112">S_OK</span></span>|<span data-ttu-id="e41f7-113">`CreateSemaphore` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="e41f7-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="e41f7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e41f7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e41f7-115">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e41f7-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e41f7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e41f7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e41f7-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="e41f7-117">The call timed out.</span></span>|  
|<span data-ttu-id="e41f7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e41f7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e41f7-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e41f7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e41f7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e41f7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e41f7-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="e41f7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e41f7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e41f7-122">E_FAIL</span></span>|<span data-ttu-id="e41f7-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e41f7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e41f7-124">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e41f7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e41f7-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e41f7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e41f7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e41f7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e41f7-127">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="e41f7-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e41f7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e41f7-128">Remarks</span></span>  
 <span data-ttu-id="e41f7-129">`CreateSemaphore` função de espelhos do Win32 que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="e41f7-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="e41f7-130">O `dwInitial` e `dwMax` parâmetros usam a mesma semântica para a contagem de semáforo como Win32 `lInitialCount` e `lMaximumCount` parâmetros, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e41f7-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="e41f7-131">`dwInitial` deve estar entre zero e `dwMax`, inclusive.</span><span class="sxs-lookup"><span data-stu-id="e41f7-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="e41f7-132">`dwMax` Deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="e41f7-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e41f7-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e41f7-133">Requirements</span></span>  
 <span data-ttu-id="e41f7-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e41f7-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e41f7-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e41f7-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e41f7-136">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e41f7-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e41f7-137">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e41f7-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41f7-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e41f7-138">See Also</span></span>  
 [<span data-ttu-id="e41f7-139">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="e41f7-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e41f7-140">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="e41f7-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="e41f7-141">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="e41f7-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
