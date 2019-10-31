---
title: Método IHostGCManager::SuspensionStarting
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
ms.openlocfilehash: bf1b830f55110c00356527bc9caa41dfd94ae377
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130462"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="eaded-102">Método IHostGCManager::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="eaded-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="eaded-103">Notifica o host que o Common Language Runtime (CLR) está suspendendo a execução de tarefas, para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="eaded-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaded-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eaded-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="eaded-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="eaded-105">Return Value</span></span>  
  
|<span data-ttu-id="eaded-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eaded-106">HRESULT</span></span>|<span data-ttu-id="eaded-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eaded-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eaded-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="eaded-108">S_OK</span></span>|<span data-ttu-id="eaded-109">`SuspensionStarting` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="eaded-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="eaded-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eaded-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eaded-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="eaded-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eaded-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eaded-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eaded-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="eaded-113">The call timed out.</span></span>|  
|<span data-ttu-id="eaded-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eaded-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eaded-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="eaded-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eaded-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eaded-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eaded-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="eaded-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eaded-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eaded-118">E_FAIL</span></span>|<span data-ttu-id="eaded-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="eaded-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eaded-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="eaded-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eaded-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eaded-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaded-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="eaded-122">Remarks</span></span>  
 <span data-ttu-id="eaded-123">O CLR chama `SuspensionStarting` para informar ao host que a coleta de lixo está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="eaded-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eaded-124">Não reagende esta tarefa.</span><span class="sxs-lookup"><span data-stu-id="eaded-124">Do not reschedule this task.</span></span> <span data-ttu-id="eaded-125">O host deve reagendar uma tarefa quando [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="eaded-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaded-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eaded-126">Requirements</span></span>  
 <span data-ttu-id="eaded-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaded-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaded-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eaded-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eaded-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eaded-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaded-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaded-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaded-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaded-131">See also</span></span>

- [<span data-ttu-id="eaded-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="eaded-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="eaded-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="eaded-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="eaded-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="eaded-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="eaded-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="eaded-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="eaded-136">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="eaded-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
