---
title: "Método ICLRTask::NeedsPriorityScheduling"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.NeedsPriorityScheduling
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 46da785535bef3443a1b917a5fb997e8e6ef3fa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="f91f3-102">Método ICLRTask::NeedsPriorityScheduling</span><span class="sxs-lookup"><span data-stu-id="f91f3-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="f91f3-103">Obtém um valor que indica se a tarefa atual, que está sendo alternada, precisa ser marcado como prioridade alta para reagendamento.</span><span class="sxs-lookup"><span data-stu-id="f91f3-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f91f3-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f91f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f91f3-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="f91f3-106">[out] `true`, se o host deve tentar reagendar a instância atual da tarefa assim que possível; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f91f3-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f91f3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f91f3-107">Return Value</span></span>  
  
|<span data-ttu-id="f91f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f91f3-108">HRESULT</span></span>|<span data-ttu-id="f91f3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f91f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f91f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f91f3-110">S_OK</span></span>|<span data-ttu-id="f91f3-111">`NeedsPriorityRescheduling`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="f91f3-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="f91f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f91f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f91f3-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f91f3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f91f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f91f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f91f3-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="f91f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="f91f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f91f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f91f3-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f91f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f91f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f91f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f91f3-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="f91f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f91f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f91f3-120">E_FAIL</span></span>|<span data-ttu-id="f91f3-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f91f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f91f3-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f91f3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f91f3-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f91f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f91f3-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f91f3-124">Remarks</span></span>  
 <span data-ttu-id="f91f3-125">Em situações em que a tarefa é quase sendo coletados pelo coletor de lixo, o CLR define o valor de `pbNeedsPriorityScheduling` para `true`, indicando o reagendamento de alta prioridade.</span><span class="sxs-lookup"><span data-stu-id="f91f3-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="f91f3-126">Isso permite que o host replanejar a tarefa rapidamente, assim, minimizar a possibilidade de atrasos na coleta de lixo e permitir que o host e o tempo de execução cooperam para conservar recursos de memória.</span><span class="sxs-lookup"><span data-stu-id="f91f3-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f91f3-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f91f3-127">Requirements</span></span>  
 <span data-ttu-id="f91f3-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f91f3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f91f3-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f91f3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f91f3-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f91f3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f91f3-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f91f3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91f3-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f91f3-132">See Also</span></span>  
 [<span data-ttu-id="f91f3-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f91f3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f91f3-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f91f3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f91f3-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f91f3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f91f3-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f91f3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
