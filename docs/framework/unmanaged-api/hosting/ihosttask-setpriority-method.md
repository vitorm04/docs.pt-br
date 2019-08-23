---
title: Método IHostTask::SetPriority
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 533e3d715b46b4ef6d473795a010fa3ad297ded2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913745"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="ac22c-102">Método IHostTask::SetPriority</span><span class="sxs-lookup"><span data-stu-id="ac22c-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="ac22c-103">Solicita que o host ajuste o nível de prioridade de thread para a tarefa representada pela instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="ac22c-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac22c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac22c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac22c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac22c-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="ac22c-106">no Um inteiro que representa o valor de prioridade de thread solicitado para a tarefa representada pela `IHostTask` instância atual.</span><span class="sxs-lookup"><span data-stu-id="ac22c-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac22c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac22c-107">Return Value</span></span>  
  
|<span data-ttu-id="ac22c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac22c-108">HRESULT</span></span>|<span data-ttu-id="ac22c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac22c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac22c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac22c-110">S_OK</span></span>|<span data-ttu-id="ac22c-111">`SetPriority`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac22c-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="ac22c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac22c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac22c-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac22c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac22c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac22c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac22c-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="ac22c-115">The call timed out.</span></span>|  
|<span data-ttu-id="ac22c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac22c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac22c-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ac22c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac22c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac22c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac22c-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="ac22c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac22c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac22c-120">E_FAIL</span></span>|<span data-ttu-id="ac22c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ac22c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac22c-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="ac22c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac22c-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac22c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac22c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac22c-124">Remarks</span></span>  
 <span data-ttu-id="ac22c-125">Os threads recebem o tempo de processamento usando um sistema Round Robin que é parcialmente baseado no nível de prioridade de um thread.</span><span class="sxs-lookup"><span data-stu-id="ac22c-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="ac22c-126">`SetPriority`permite que o CLR defina o nível de prioridade do thread para a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="ac22c-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="ac22c-127">Há suporte `newPriority` para os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac22c-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="ac22c-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="ac22c-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="ac22c-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="ac22c-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="ac22c-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="ac22c-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="ac22c-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="ac22c-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="ac22c-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="ac22c-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="ac22c-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="ac22c-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="ac22c-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="ac22c-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="ac22c-135">O CLR chama `SetPriority` quando o valor <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> de é modificado pelo código do usuário.</span><span class="sxs-lookup"><span data-stu-id="ac22c-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="ac22c-136">Um host pode definir seus próprios algoritmos para atribuição de prioridade de thread e é livre para ignorar essa solicitação.</span><span class="sxs-lookup"><span data-stu-id="ac22c-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac22c-137">`SetPriority`não relata se o nível de prioridade do thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="ac22c-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="ac22c-138">Chame [IHostTask::](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) getanteriory para determinar o valor do nível de prioridade de thread da tarefa.</span><span class="sxs-lookup"><span data-stu-id="ac22c-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="ac22c-139">Os valores de nível de prioridade de thread são `SetThreadPriority` definidos pela função do Win32.</span><span class="sxs-lookup"><span data-stu-id="ac22c-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="ac22c-140">Para obter mais informações sobre prioridade de thread, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="ac22c-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac22c-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac22c-141">Requirements</span></span>  
 <span data-ttu-id="ac22c-142">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac22c-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac22c-143">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac22c-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac22c-144">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ac22c-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac22c-145">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac22c-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac22c-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac22c-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="ac22c-147">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="ac22c-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ac22c-148">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="ac22c-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ac22c-149">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="ac22c-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ac22c-150">Método GetPriority</span><span class="sxs-lookup"><span data-stu-id="ac22c-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="ac22c-151">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="ac22c-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
