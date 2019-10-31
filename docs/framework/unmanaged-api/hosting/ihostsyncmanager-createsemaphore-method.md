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
ms.openlocfilehash: 02066d3923714e66bf287f1435b7854280c97cb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195828"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="9f0e2-102">Método IHostSyncManager::CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="9f0e2-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="9f0e2-103">Cria um objeto [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) para o Common Language Runtime (CLR) a ser usado como um semáforo para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f0e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f0e2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f0e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f0e2-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="9f0e2-106">no A contagem inicial para `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="9f0e2-107">no A contagem máxima de `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="9f0e2-108">fora Um ponteiro para o endereço de uma instância de `IHostSemaphore`, ou NULL se o semáforo não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f0e2-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9f0e2-109">Return Value</span></span>  
  
|<span data-ttu-id="9f0e2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f0e2-110">HRESULT</span></span>|<span data-ttu-id="9f0e2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f0e2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f0e2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f0e2-112">S_OK</span></span>|<span data-ttu-id="9f0e2-113">`CreateSemaphore` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="9f0e2-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f0e2-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f0e2-115">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9f0e2-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f0e2-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9f0e2-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-117">The call timed out.</span></span>|  
|<span data-ttu-id="9f0e2-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9f0e2-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9f0e2-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9f0e2-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9f0e2-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9f0e2-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9f0e2-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9f0e2-122">E_FAIL</span></span>|<span data-ttu-id="9f0e2-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9f0e2-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9f0e2-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9f0e2-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9f0e2-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9f0e2-127">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f0e2-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f0e2-128">Remarks</span></span>  
 <span data-ttu-id="9f0e2-129">`CreateSemaphore` espelha a função do Win32 que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="9f0e2-130">Os parâmetros `dwInitial` e `dwMax` usam a mesma semântica para a contagem de semáforos como os parâmetros de `lInitialCount` e `lMaximumCount` do Win32, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="9f0e2-131">`dwInitial` deve estar entre zero e `dwMax`, inclusive.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="9f0e2-132">`dwMax` deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="9f0e2-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f0e2-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f0e2-133">Requirements</span></span>  
 <span data-ttu-id="9f0e2-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f0e2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f0e2-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9f0e2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f0e2-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9f0e2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f0e2-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f0e2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f0e2-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f0e2-138">See also</span></span>

- [<span data-ttu-id="9f0e2-139">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="9f0e2-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9f0e2-140">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="9f0e2-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="9f0e2-141">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="9f0e2-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
