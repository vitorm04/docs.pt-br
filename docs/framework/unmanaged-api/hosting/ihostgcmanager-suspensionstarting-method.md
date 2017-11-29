---
title: "Método IHostGCManager::SuspensionStarting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.SuspensionStarting
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c807a124570f38922509d27e52936b980e36fba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="690c8-102">Método IHostGCManager::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="690c8-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="690c8-103">Notifica o host que o common language runtime (CLR) está suspendendo a execução de tarefas, para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="690c8-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="690c8-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="690c8-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="690c8-105">Return Value</span></span>  
  
|<span data-ttu-id="690c8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="690c8-106">HRESULT</span></span>|<span data-ttu-id="690c8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="690c8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="690c8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="690c8-108">S_OK</span></span>|<span data-ttu-id="690c8-109">`SuspensionStarting`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="690c8-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="690c8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="690c8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="690c8-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="690c8-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="690c8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="690c8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="690c8-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="690c8-113">The call timed out.</span></span>|  
|<span data-ttu-id="690c8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="690c8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="690c8-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="690c8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="690c8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="690c8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="690c8-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="690c8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="690c8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="690c8-118">E_FAIL</span></span>|<span data-ttu-id="690c8-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="690c8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="690c8-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="690c8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="690c8-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="690c8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="690c8-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="690c8-122">Remarks</span></span>  
 <span data-ttu-id="690c8-123">O CLR chama `SuspensionStarting` para informar o host que está ocorrendo a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="690c8-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="690c8-124">Não reagende esta tarefa.</span><span class="sxs-lookup"><span data-stu-id="690c8-124">Do not reschedule this task.</span></span> <span data-ttu-id="690c8-125">O host deve reagendar uma tarefa quando [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="690c8-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="690c8-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="690c8-126">Requirements</span></span>  
 <span data-ttu-id="690c8-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="690c8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="690c8-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="690c8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="690c8-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="690c8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="690c8-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="690c8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690c8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="690c8-131">See Also</span></span>  
 [<span data-ttu-id="690c8-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="690c8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="690c8-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="690c8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="690c8-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="690c8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="690c8-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="690c8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="690c8-136">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="690c8-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
