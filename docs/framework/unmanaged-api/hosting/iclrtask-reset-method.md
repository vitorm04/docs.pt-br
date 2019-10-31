---
title: Método ICLRTask::Reset
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124636"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="dec00-102">Método ICLRTask::Reset</span><span class="sxs-lookup"><span data-stu-id="dec00-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="dec00-103">Informa o Common Language Runtime (CLR) que o host concluiu uma tarefa e permite que o CLR reutilize a instância [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual para representar outra tarefa.</span><span class="sxs-lookup"><span data-stu-id="dec00-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dec00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dec00-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dec00-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dec00-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="dec00-106">[in] `true`, se o tempo de execução deve redefinir todos os valores estáticos relacionados ao thread, além das informações de segurança e localidade relacionadas à instância de `ICLRTask` atual; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="dec00-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="dec00-107">Se o valor for `true`, o tempo de execução redefinirá os dados que foram armazenados usando <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="dec00-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dec00-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dec00-108">Return Value</span></span>  
  
|<span data-ttu-id="dec00-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dec00-109">HRESULT</span></span>|<span data-ttu-id="dec00-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="dec00-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dec00-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dec00-111">S_OK</span></span>|<span data-ttu-id="dec00-112">`Reset` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dec00-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="dec00-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dec00-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dec00-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada.</span><span class="sxs-lookup"><span data-stu-id="dec00-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="dec00-115">com êxito</span><span class="sxs-lookup"><span data-stu-id="dec00-115">successfully</span></span>|  
|<span data-ttu-id="dec00-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dec00-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dec00-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="dec00-117">The call timed out.</span></span>|  
|<span data-ttu-id="dec00-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dec00-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dec00-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="dec00-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dec00-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dec00-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dec00-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="dec00-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dec00-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dec00-122">E_FAIL</span></span>|<span data-ttu-id="dec00-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dec00-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dec00-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="dec00-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dec00-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dec00-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dec00-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="dec00-126">Remarks</span></span>  
 <span data-ttu-id="dec00-127">O CLR pode reciclar instâncias de `ICLRTask` criadas anteriormente para evitar a sobrecarga de criar novas instâncias repetidamente toda vez que precisar de uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="dec00-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="dec00-128">O host habilita esse recurso chamando `ICLRTask::Reset` em vez de [ICLRTask:: ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) quando tiver concluído uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="dec00-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="dec00-129">A lista a seguir resume o ciclo de vida normal de uma instância de `ICLRTask`:</span><span class="sxs-lookup"><span data-stu-id="dec00-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="dec00-130">O tempo de execução cria uma nova instância de `ICLRTask`.</span><span class="sxs-lookup"><span data-stu-id="dec00-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="dec00-131">O tempo de execução chama [IHostTaskManager:: GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) para obter uma referência à tarefa de host atual.</span><span class="sxs-lookup"><span data-stu-id="dec00-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="dec00-132">O tempo de execução chama [IHostTask:: SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) para associar a nova instância à tarefa do host.</span><span class="sxs-lookup"><span data-stu-id="dec00-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="dec00-133">A tarefa é executada e concluída.</span><span class="sxs-lookup"><span data-stu-id="dec00-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="dec00-134">O host destrói a tarefa chamando `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="dec00-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="dec00-135">`Reset` altera esse cenário de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="dec00-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="dec00-136">Na etapa 5 acima, o host chama `Reset` para redefinir a tarefa para um estado limpo e, em seguida, dissocia a instância `ICLRTask` de sua instância [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) associada.</span><span class="sxs-lookup"><span data-stu-id="dec00-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="dec00-137">Se desejar, o host também pode armazenar em cache a instância de `IHostTask` para reutilização.</span><span class="sxs-lookup"><span data-stu-id="dec00-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="dec00-138">Na etapa 1 acima, o tempo de execução efetua pull de um `ICLRTask` reciclado do cache em vez de criar uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="dec00-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="dec00-139">Essa abordagem funciona bem quando o host também tem um pool de tarefas de trabalho reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="dec00-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="dec00-140">Quando o host destrói uma de suas instâncias de `IHostTask`, ele destrói o `ICLRTask` correspondente chamando `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="dec00-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dec00-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dec00-141">Requirements</span></span>  
 <span data-ttu-id="dec00-142">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dec00-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dec00-143">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dec00-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dec00-144">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dec00-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dec00-145">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dec00-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dec00-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dec00-146">See also</span></span>

- [<span data-ttu-id="dec00-147">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="dec00-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="dec00-148">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="dec00-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dec00-149">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="dec00-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dec00-150">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="dec00-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
