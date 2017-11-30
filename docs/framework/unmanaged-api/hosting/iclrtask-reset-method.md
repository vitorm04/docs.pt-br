---
title: "Método ICLRTask::Reset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c50dc4770665e2b049f41a105b58231221b8e9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="4a076-102">Método ICLRTask::Reset</span><span class="sxs-lookup"><span data-stu-id="4a076-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="4a076-103">Informa o common language runtime (CLR) que o host concluiu uma tarefa e habilita o CLR reutilizar atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância para representar outra tarefa.</span><span class="sxs-lookup"><span data-stu-id="4a076-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a076-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a076-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a076-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a076-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="4a076-106">[in] `true`, se o tempo de execução deve restaurar todos os relacionados ao thread estático valores além das informações de segurança e a localidade relacionadas à atual `ICLRTask` instância; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="4a076-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="4a076-107">Se o valor for `true`, o tempo de execução redefine os dados que foram armazenados usando <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a076-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a076-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4a076-108">Return Value</span></span>  
  
|<span data-ttu-id="4a076-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a076-109">HRESULT</span></span>|<span data-ttu-id="4a076-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a076-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a076-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a076-111">S_OK</span></span>|<span data-ttu-id="4a076-112">`Reset`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="4a076-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="4a076-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a076-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a076-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada.</span><span class="sxs-lookup"><span data-stu-id="4a076-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="4a076-115">com êxito</span><span class="sxs-lookup"><span data-stu-id="4a076-115">successfully</span></span>|  
|<span data-ttu-id="4a076-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a076-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a076-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="4a076-117">The call timed out.</span></span>|  
|<span data-ttu-id="4a076-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a076-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a076-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4a076-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a076-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a076-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a076-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="4a076-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a076-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a076-122">E_FAIL</span></span>|<span data-ttu-id="4a076-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4a076-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a076-124">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4a076-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a076-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a076-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a076-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a076-126">Remarks</span></span>  
 <span data-ttu-id="4a076-127">O CLR pode reciclar criado anteriormente `ICLRTask` instâncias para evitar a sobrecarga de repetidamente criando novas instâncias toda vez que ele precisa de uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="4a076-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="4a076-128">O host habilita esse recurso chamando `ICLRTask::Reset` em vez de [: Exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) quando ela estiver concluída, uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="4a076-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="4a076-129">A lista a seguir resume o ciclo de vida normal de uma `ICLRTask` instância:</span><span class="sxs-lookup"><span data-stu-id="4a076-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="4a076-130">O tempo de execução cria um novo `ICLRTask` instância.</span><span class="sxs-lookup"><span data-stu-id="4a076-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="4a076-131">O tempo de execução chama [Getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) para obter uma referência para a tarefa de host atual.</span><span class="sxs-lookup"><span data-stu-id="4a076-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="4a076-132">O tempo de execução chama [: Setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) para associar a nova instância da tarefa de host.</span><span class="sxs-lookup"><span data-stu-id="4a076-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="4a076-133">A tarefa executa e concluído.</span><span class="sxs-lookup"><span data-stu-id="4a076-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="4a076-134">O host destrói a tarefa chamando `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="4a076-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="4a076-135">`Reset`altera esse cenário de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="4a076-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="4a076-136">Na etapa 5 acima, as chamadas de host `Reset` para redefinir a tarefa para um estado limpo e, em seguida, separa o `ICLRTask` instância de seus associados [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="4a076-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="4a076-137">Se desejado, o host também pode armazenar a `IHostTask` instância para reutilização.</span><span class="sxs-lookup"><span data-stu-id="4a076-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="4a076-138">Na etapa 1 acima, o tempo de execução recebe uma reciclagem `ICLRTask` do cache em vez de criar uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="4a076-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="4a076-139">Essa abordagem funciona bem quando o host também tem um conjunto de tarefas de trabalho reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="4a076-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="4a076-140">Quando o host destrói um dos seus `IHostTask` instâncias, ele destrói correspondente `ICLRTask` chamando `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="4a076-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a076-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a076-141">Requirements</span></span>  
 <span data-ttu-id="4a076-142">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a076-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a076-143">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a076-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a076-144">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4a076-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a076-145">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a076-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a076-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a076-146">See Also</span></span>  
 [<span data-ttu-id="4a076-147">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="4a076-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4a076-148">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="4a076-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4a076-149">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="4a076-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4a076-150">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="4a076-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
