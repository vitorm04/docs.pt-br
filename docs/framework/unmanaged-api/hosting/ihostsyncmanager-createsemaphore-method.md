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
ms.openlocfilehash: 680280e959d523356b95a5a4d9390c80720c0330
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803134"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="48958-102">Método IHostSyncManager::CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="48958-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="48958-103">Cria um objeto [IHostSemaphore](ihostsemaphore-interface.md) para o Common Language Runtime (CLR) a ser usado como um semáforo para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="48958-103">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48958-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48958-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48958-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48958-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="48958-106">no A contagem inicial para `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="48958-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="48958-107">no A contagem máxima para `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="48958-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="48958-108">fora Um ponteiro para o endereço de uma `IHostSemaphore` instância ou NULL se o semáforo não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="48958-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48958-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="48958-109">Return Value</span></span>  
  
|<span data-ttu-id="48958-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48958-110">HRESULT</span></span>|<span data-ttu-id="48958-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="48958-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48958-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="48958-112">S_OK</span></span>|<span data-ttu-id="48958-113">`CreateSemaphore`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="48958-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="48958-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48958-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48958-115">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="48958-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48958-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48958-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48958-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="48958-117">The call timed out.</span></span>|  
|<span data-ttu-id="48958-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48958-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48958-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="48958-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48958-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48958-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48958-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="48958-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48958-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48958-122">E_FAIL</span></span>|<span data-ttu-id="48958-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="48958-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48958-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="48958-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48958-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="48958-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="48958-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="48958-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="48958-127">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="48958-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48958-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="48958-128">Remarks</span></span>  
 <span data-ttu-id="48958-129">`CreateSemaphore`espelha a função do Win32 que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="48958-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="48958-130">Os `dwInitial` `dwMax` parâmetros e usam a mesma semântica para a contagem de semáforos como o Win32 `lInitialCount` e os `lMaximumCount` parâmetros, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="48958-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="48958-131">`dwInitial`deve estar entre zero e `dwMax` , inclusive.</span><span class="sxs-lookup"><span data-stu-id="48958-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="48958-132">`dwMax`deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="48958-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48958-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48958-133">Requirements</span></span>  
 <span data-ttu-id="48958-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48958-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48958-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48958-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48958-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48958-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48958-137">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48958-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48958-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="48958-138">See also</span></span>

- [<span data-ttu-id="48958-139">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="48958-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="48958-140">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="48958-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="48958-141">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="48958-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
