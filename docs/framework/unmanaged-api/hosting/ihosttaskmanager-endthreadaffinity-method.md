---
title: "Método IHostTaskManager::EndThreadAffinity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EndThreadAffinity
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3b1c67397408253a11a12263ea9c9b45429a133
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="f93d1-102">Método IHostTaskManager::EndThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="f93d1-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="f93d1-103">Notifica o host que o código gerenciado está saindo do período em que a tarefa atual não deve ser movida para outro thread do sistema operacional, após uma chamada anterior para [BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="f93d1-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f93d1-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f93d1-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f93d1-105">Return Value</span></span>  
  
|<span data-ttu-id="f93d1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f93d1-106">HRESULT</span></span>|<span data-ttu-id="f93d1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f93d1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f93d1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f93d1-108">S_OK</span></span>|<span data-ttu-id="f93d1-109">`EndThreadAffinity`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="f93d1-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="f93d1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f93d1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f93d1-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f93d1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f93d1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f93d1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f93d1-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="f93d1-113">The call timed out.</span></span>|  
|<span data-ttu-id="f93d1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f93d1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f93d1-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f93d1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f93d1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f93d1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f93d1-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="f93d1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f93d1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f93d1-118">E_FAIL</span></span>|<span data-ttu-id="f93d1-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f93d1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f93d1-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f93d1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f93d1-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f93d1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f93d1-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="f93d1-122">E_UNEXPECTED</span></span>|<span data-ttu-id="f93d1-123">`EndThreadAffinity`foi chamado sem uma chamada anterior correspondente para `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="f93d1-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f93d1-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f93d1-124">Remarks</span></span>  
 <span data-ttu-id="f93d1-125">O CLR faz uma chamada correspondente para `BeginThreadAffinity` da tarefa atual antes de chamar `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="f93d1-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="f93d1-126">Na ausência de tal chamada correspondente, a implementação do host de [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) devem retornar E_UNEXPECTED e não executar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="f93d1-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f93d1-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f93d1-127">Requirements</span></span>  
 <span data-ttu-id="f93d1-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f93d1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f93d1-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f93d1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f93d1-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f93d1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f93d1-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93d1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93d1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f93d1-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="f93d1-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f93d1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f93d1-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f93d1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f93d1-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f93d1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f93d1-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f93d1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
