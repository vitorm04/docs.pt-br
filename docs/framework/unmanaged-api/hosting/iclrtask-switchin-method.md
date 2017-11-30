---
title: "Método ICLRTask::SwitchIn"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SwitchIn
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 01e91c4febfebf8ec8ffd4c0ffbf8e33a4ff0edd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="5c790-102">Método ICLRTask::SwitchIn</span><span class="sxs-lookup"><span data-stu-id="5c790-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="5c790-103">Notifica o common language runtime (CLR) que a tarefa que atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância representa agora está em um estado operacional.</span><span class="sxs-lookup"><span data-stu-id="5c790-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c790-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c790-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c790-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c790-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="5c790-106">[in] Um identificador para o thread físico no qual a tarefa é representado por atual `ICLRTask` instância está em execução.</span><span class="sxs-lookup"><span data-stu-id="5c790-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c790-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5c790-107">Return Value</span></span>  
  
|<span data-ttu-id="5c790-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c790-108">HRESULT</span></span>|<span data-ttu-id="5c790-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c790-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c790-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c790-110">S_OK</span></span>|<span data-ttu-id="5c790-111">`SwitchIn`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="5c790-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="5c790-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c790-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c790-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5c790-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c790-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c790-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c790-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="5c790-115">The call timed out.</span></span>|  
|<span data-ttu-id="5c790-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c790-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c790-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5c790-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c790-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c790-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c790-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="5c790-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c790-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c790-120">E_FAIL</span></span>|<span data-ttu-id="5c790-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5c790-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c790-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="5c790-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c790-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c790-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5c790-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="5c790-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="5c790-125">`SwitchIn`foi chamado sem uma chamada anterior para [método SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c790-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c790-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c790-126">Remarks</span></span>  
 <span data-ttu-id="5c790-127">O `threadHandle` parâmetro representa um identificador para o thread de sistema operacional no qual a tarefa é representado por atual `ICLRTask` instância foi agendada.</span><span class="sxs-lookup"><span data-stu-id="5c790-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="5c790-128">Se a representação ocorreu neste thread, você deve chamar [Ihostsecuritymanager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) antes de alternar na tarefa.</span><span class="sxs-lookup"><span data-stu-id="5c790-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c790-129">Uma chamada para `SwitchIn` sem uma chamada anterior para `SwitchOut` falhará com um valor HRESULT de HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="5c790-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c790-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c790-130">Requirements</span></span>  
 <span data-ttu-id="5c790-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c790-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c790-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c790-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c790-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5c790-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c790-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c790-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c790-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c790-135">See Also</span></span>  
 [<span data-ttu-id="5c790-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="5c790-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="5c790-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="5c790-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="5c790-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="5c790-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="5c790-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="5c790-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
