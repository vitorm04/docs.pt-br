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
ms.openlocfilehash: cf9ecdeb4df6210805490586f1818298025fc036
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749944"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="853f1-102">Método IHostTask::SetPriority</span><span class="sxs-lookup"><span data-stu-id="853f1-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="853f1-103">Solicitações que o host de ajustar a prioridade do thread de nível para a tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="853f1-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="853f1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="853f1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="853f1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="853f1-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="853f1-106">[in] Um inteiro que representa o valor de prioridade de thread solicitada para a tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="853f1-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="853f1-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="853f1-107">Return Value</span></span>  
  
|<span data-ttu-id="853f1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="853f1-108">HRESULT</span></span>|<span data-ttu-id="853f1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="853f1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="853f1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="853f1-110">S_OK</span></span>|<span data-ttu-id="853f1-111">`SetPriority` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="853f1-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="853f1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="853f1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="853f1-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="853f1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="853f1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="853f1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="853f1-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="853f1-115">The call timed out.</span></span>|  
|<span data-ttu-id="853f1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="853f1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="853f1-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="853f1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="853f1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="853f1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="853f1-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="853f1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="853f1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="853f1-120">E_FAIL</span></span>|<span data-ttu-id="853f1-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="853f1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="853f1-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="853f1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="853f1-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="853f1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="853f1-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="853f1-124">Remarks</span></span>  
 <span data-ttu-id="853f1-125">Threads de processamento são concedidas tempo usando um sistema de rodízio parcialmente com base no nível de prioridade do thread.</span><span class="sxs-lookup"><span data-stu-id="853f1-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="853f1-126">`SetPriority` permite que o CLR definir esse nível de prioridade de thread para a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="853f1-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="853f1-127">O seguinte `newPriority` valores têm suporte.</span><span class="sxs-lookup"><span data-stu-id="853f1-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="853f1-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="853f1-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="853f1-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="853f1-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="853f1-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="853f1-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="853f1-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="853f1-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="853f1-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="853f1-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="853f1-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="853f1-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="853f1-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="853f1-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="853f1-135">O CLR chama `SetPriority` quando o valor da <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> é modificado pelo código do usuário.</span><span class="sxs-lookup"><span data-stu-id="853f1-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="853f1-136">Um host pode definir seus próprios algoritmos para atribuição de prioridade de thread e está livre para ignorar essa solicitação.</span><span class="sxs-lookup"><span data-stu-id="853f1-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="853f1-137">`SetPriority` não relata se o nível de prioridade de thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="853f1-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="853f1-138">Chame [ihosttask:: Getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) para determinar o valor do nível de prioridade do thread da tarefa.</span><span class="sxs-lookup"><span data-stu-id="853f1-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="853f1-139">Valores de nível de prioridade de thread são definidos pelo Win32 `SetThreadPriority` função.</span><span class="sxs-lookup"><span data-stu-id="853f1-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="853f1-140">Para obter mais informações sobre a prioridade de thread, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="853f1-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="853f1-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="853f1-141">Requirements</span></span>  
 <span data-ttu-id="853f1-142">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="853f1-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="853f1-143">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="853f1-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="853f1-144">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="853f1-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="853f1-145">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="853f1-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853f1-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="853f1-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="853f1-147">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="853f1-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="853f1-148">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="853f1-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="853f1-149">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="853f1-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="853f1-150">Método GetPriority</span><span class="sxs-lookup"><span data-stu-id="853f1-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="853f1-151">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="853f1-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
