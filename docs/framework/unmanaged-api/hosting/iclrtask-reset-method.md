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
ms.openlocfilehash: 15004238ee296e44ae77cd8739b7f62ea2a7a100
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762962"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="d41be-102">Método ICLRTask::Reset</span><span class="sxs-lookup"><span data-stu-id="d41be-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="d41be-103">Informa o Common Language Runtime (CLR) que o host concluiu uma tarefa e permite que o CLR reutilize a instância [ICLRTask](iclrtask-interface.md) atual para representar outra tarefa.</span><span class="sxs-lookup"><span data-stu-id="d41be-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d41be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d41be-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d41be-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d41be-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="d41be-106">[in] `true` , se o tempo de execução deve redefinir todos os valores estáticos relacionados ao thread, além das informações de segurança e localidade relacionadas à `ICLRTask` instância atual; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="d41be-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="d41be-107">Se o valor for `true` , o tempo de execução redefinirá os dados que foram armazenados usando o <xref:System.Threading.Thread.AllocateDataSlot%2A> ou o <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .</span><span class="sxs-lookup"><span data-stu-id="d41be-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d41be-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="d41be-108">Return Value</span></span>  
  
|<span data-ttu-id="d41be-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d41be-109">HRESULT</span></span>|<span data-ttu-id="d41be-110">Description</span><span class="sxs-lookup"><span data-stu-id="d41be-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d41be-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d41be-111">S_OK</span></span>|<span data-ttu-id="d41be-112">`Reset`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d41be-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="d41be-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d41be-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d41be-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada.</span><span class="sxs-lookup"><span data-stu-id="d41be-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="d41be-115">com êxito</span><span class="sxs-lookup"><span data-stu-id="d41be-115">successfully</span></span>|  
|<span data-ttu-id="d41be-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d41be-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d41be-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d41be-117">The call timed out.</span></span>|  
|<span data-ttu-id="d41be-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d41be-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d41be-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d41be-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d41be-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d41be-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d41be-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="d41be-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d41be-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d41be-122">E_FAIL</span></span>|<span data-ttu-id="d41be-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d41be-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d41be-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="d41be-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d41be-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d41be-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d41be-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="d41be-126">Remarks</span></span>  
 <span data-ttu-id="d41be-127">O CLR pode reciclar instâncias criadas anteriormente `ICLRTask` para evitar a sobrecarga de criar novas instâncias repetidamente toda vez que precisar de uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="d41be-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="d41be-128">O host habilita esse recurso chamando `ICLRTask::Reset` em vez de [ICLRTask:: ExitTask](iclrtask-exittask-method.md) quando concluiu uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="d41be-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="d41be-129">A lista a seguir resume o ciclo de vida normal de uma `ICLRTask` instância do:</span><span class="sxs-lookup"><span data-stu-id="d41be-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="d41be-130">O tempo de execução cria uma nova `ICLRTask` instância.</span><span class="sxs-lookup"><span data-stu-id="d41be-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="d41be-131">O tempo de execução chama [IHostTaskManager:: GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) para obter uma referência à tarefa de host atual.</span><span class="sxs-lookup"><span data-stu-id="d41be-131">The runtime calls [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="d41be-132">O tempo de execução chama [IHostTask:: SetCLRTask](ihosttask-setclrtask-method.md) para associar a nova instância à tarefa do host.</span><span class="sxs-lookup"><span data-stu-id="d41be-132">The runtime calls [IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="d41be-133">A tarefa é executada e concluída.</span><span class="sxs-lookup"><span data-stu-id="d41be-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="d41be-134">O host destrói a tarefa chamando `ICLRTask::ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="d41be-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="d41be-135">`Reset`altera esse cenário de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="d41be-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="d41be-136">Na etapa 5 acima, o host chama `Reset` para redefinir a tarefa para um estado limpo e, em seguida, dissocia a `ICLRTask` instância de sua instância [IHostTask](ihosttask-interface.md) associada.</span><span class="sxs-lookup"><span data-stu-id="d41be-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](ihosttask-interface.md) instance.</span></span> <span data-ttu-id="d41be-137">Se desejar, o host também pode armazenar em cache a `IHostTask` instância para reutilização.</span><span class="sxs-lookup"><span data-stu-id="d41be-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="d41be-138">Na etapa 1 acima, o tempo de execução efetua pull `ICLRTask` de uma reciclagem do cache em vez de criar uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="d41be-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="d41be-139">Essa abordagem funciona bem quando o host também tem um pool de tarefas de trabalho reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="d41be-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="d41be-140">Quando o host destrói uma de suas `IHostTask` instâncias, ele destrói o correspondente `ICLRTask` chamando `ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="d41be-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d41be-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d41be-141">Requirements</span></span>  
 <span data-ttu-id="d41be-142">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d41be-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d41be-143">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d41be-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d41be-144">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d41be-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d41be-145">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d41be-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41be-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="d41be-146">See also</span></span>

- [<span data-ttu-id="d41be-147">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d41be-147">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d41be-148">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d41be-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d41be-149">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="d41be-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d41be-150">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d41be-150">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
