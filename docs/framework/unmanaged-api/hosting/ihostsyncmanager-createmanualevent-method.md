---
title: Método IHostSyncManager::CreateManualEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 13679b4d40e660dfdd18e6fbafe19226b2ffda37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195863"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="0deba-102">Método IHostSyncManager::CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="0deba-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="0deba-103">Cria um objeto de evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="0deba-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0deba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0deba-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0deba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0deba-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="0deba-106">[in] `true`, se o objeto for sinalizado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0deba-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="0deba-107">fora Um ponteiro para o endereço de uma instância de [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) ou NULL se o evento não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="0deba-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0deba-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0deba-108">Return Value</span></span>  
  
|<span data-ttu-id="0deba-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0deba-109">HRESULT</span></span>|<span data-ttu-id="0deba-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0deba-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0deba-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0deba-111">S_OK</span></span>|<span data-ttu-id="0deba-112">`CreateManualEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0deba-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0deba-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0deba-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0deba-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0deba-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0deba-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0deba-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0deba-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0deba-116">The call timed out.</span></span>|  
|<span data-ttu-id="0deba-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0deba-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0deba-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0deba-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0deba-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0deba-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0deba-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0deba-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0deba-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0deba-121">E_FAIL</span></span>|<span data-ttu-id="0deba-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0deba-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0deba-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="0deba-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0deba-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0deba-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0deba-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0deba-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0deba-126">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="0deba-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0deba-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="0deba-127">Remarks</span></span>  
 <span data-ttu-id="0deba-128">`CreateManualEvent` cria um `IHostManualEvent`, um objeto de evento de redefinição manual que requer uma chamada para o método [IHostManualEvent:: Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) para defini-lo como um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="0deba-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="0deba-129">`CreateManualEvent` espelha a função de `CreateEvent` do Win32 com um valor de `true` especificado para o parâmetro `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="0deba-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0deba-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0deba-130">Requirements</span></span>  
 <span data-ttu-id="0deba-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0deba-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0deba-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0deba-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0deba-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0deba-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0deba-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0deba-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0deba-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0deba-135">See also</span></span>

- [<span data-ttu-id="0deba-136">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="0deba-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0deba-137">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="0deba-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="0deba-138">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="0deba-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
