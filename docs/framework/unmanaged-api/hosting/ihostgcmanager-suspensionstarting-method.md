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
ms.openlocfilehash: f2b4028c78daf266e4ffecd86e6b0b30b9607d5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804810"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="9418b-102">Método IHostGCManager::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="9418b-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="9418b-103">Notifica o host que o Common Language Runtime (CLR) está suspendendo a execução de tarefas, para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9418b-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9418b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9418b-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9418b-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9418b-105">Return Value</span></span>  
  
|<span data-ttu-id="9418b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9418b-106">HRESULT</span></span>|<span data-ttu-id="9418b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9418b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9418b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9418b-108">S_OK</span></span>|<span data-ttu-id="9418b-109">`SuspensionStarting`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9418b-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="9418b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9418b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9418b-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9418b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9418b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9418b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9418b-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9418b-113">The call timed out.</span></span>|  
|<span data-ttu-id="9418b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9418b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9418b-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9418b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9418b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9418b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9418b-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9418b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9418b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9418b-118">E_FAIL</span></span>|<span data-ttu-id="9418b-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9418b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9418b-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9418b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9418b-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9418b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9418b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9418b-122">Remarks</span></span>  
 <span data-ttu-id="9418b-123">O CLR chama `SuspensionStarting` para informar ao host que a coleta de lixo está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="9418b-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9418b-124">Não reagende esta tarefa.</span><span class="sxs-lookup"><span data-stu-id="9418b-124">Do not reschedule this task.</span></span> <span data-ttu-id="9418b-125">O host deve reagendar uma tarefa quando [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="9418b-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9418b-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9418b-126">Requirements</span></span>  
 <span data-ttu-id="9418b-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9418b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9418b-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9418b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9418b-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9418b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9418b-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9418b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9418b-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="9418b-131">See also</span></span>

- [<span data-ttu-id="9418b-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="9418b-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9418b-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="9418b-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9418b-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="9418b-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9418b-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="9418b-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9418b-136">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="9418b-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
