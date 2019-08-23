---
title: Método ICLRTask::SwitchIn
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f408dd5e4d383040d9e3c03cd5bba8ebd320610f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938363"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="0c62b-102">Método ICLRTask::SwitchIn</span><span class="sxs-lookup"><span data-stu-id="0c62b-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="0c62b-103">Notifica o Common Language Runtime (CLR) que a tarefa que a instância [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual representa agora está em um estado operável.</span><span class="sxs-lookup"><span data-stu-id="0c62b-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c62b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c62b-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c62b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c62b-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="0c62b-106">no Um identificador para o thread físico no qual a tarefa representada pela instância atual `ICLRTask` está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="0c62b-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c62b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0c62b-107">Return Value</span></span>  
  
|<span data-ttu-id="0c62b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c62b-108">HRESULT</span></span>|<span data-ttu-id="0c62b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c62b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c62b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c62b-110">S_OK</span></span>|<span data-ttu-id="0c62b-111">`SwitchIn`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0c62b-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="0c62b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c62b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c62b-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0c62b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c62b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c62b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c62b-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0c62b-115">The call timed out.</span></span>|  
|<span data-ttu-id="0c62b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c62b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c62b-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0c62b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c62b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c62b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c62b-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0c62b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c62b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c62b-120">E_FAIL</span></span>|<span data-ttu-id="0c62b-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0c62b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c62b-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="0c62b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c62b-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c62b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0c62b-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0c62b-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0c62b-125">`SwitchIn`foi chamado sem uma chamada anterior para o [método SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="0c62b-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c62b-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c62b-126">Remarks</span></span>  
 <span data-ttu-id="0c62b-127">O `threadHandle` parâmetro representa um identificador para o thread do sistema operacional no qual a tarefa representada pela instância `ICLRTask` atual foi agendada.</span><span class="sxs-lookup"><span data-stu-id="0c62b-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="0c62b-128">Se a representação tiver ocorrido neste thread, você deverá chamar [IHostSecurityManager:: RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) antes de alternar para a tarefa.</span><span class="sxs-lookup"><span data-stu-id="0c62b-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c62b-129">Uma chamada para `SwitchIn` sem uma chamada anterior para `SwitchOut` falha com um valor HRESULT de HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="0c62b-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c62b-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c62b-130">Requirements</span></span>  
 <span data-ttu-id="0c62b-131">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c62b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c62b-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c62b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c62b-133">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0c62b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c62b-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c62b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c62b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c62b-135">See also</span></span>

- [<span data-ttu-id="0c62b-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="0c62b-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0c62b-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="0c62b-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0c62b-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="0c62b-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0c62b-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="0c62b-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
