---
title: "Método IHostTaskManager::ReverseLeaveRuntime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseLeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db8a9114cd15a4e7d42e8f99941d4bcbb9faa842
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="1136a-102">Método IHostTaskManager::ReverseLeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="1136a-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="1136a-103">Notifica o host que o controle é deixar o common language runtime (CLR) e inserir uma função não gerenciada, por sua vez, chamado de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1136a-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1136a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1136a-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1136a-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1136a-105">Return Value</span></span>  
  
|<span data-ttu-id="1136a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1136a-106">HRESULT</span></span>|<span data-ttu-id="1136a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1136a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1136a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1136a-108">S_OK</span></span>|<span data-ttu-id="1136a-109">`ReverseLeaveRuntime`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="1136a-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="1136a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1136a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1136a-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1136a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1136a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1136a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1136a-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="1136a-113">The call timed out.</span></span>|  
|<span data-ttu-id="1136a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1136a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1136a-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1136a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1136a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1136a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1136a-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="1136a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1136a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1136a-118">E_FAIL</span></span>|<span data-ttu-id="1136a-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1136a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1136a-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1136a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1136a-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1136a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1136a-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1136a-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1136a-123">Não há memória suficiente está disponível para concluir a alocação de recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="1136a-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1136a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="1136a-124">Remarks</span></span>  
 <span data-ttu-id="1136a-125">O CLR chama `ReverseLeaveRuntime` para informar o host em que a tarefa em execução no momento está retornando o controle para uma função não gerenciada, por sua vez, chamado de código gerenciado por meio da plataforma invocar.</span><span class="sxs-lookup"><span data-stu-id="1136a-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="1136a-126">Cada chamada para `ReverseLeaveRuntime` corresponde a uma chamada correspondente para [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="1136a-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1136a-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1136a-127">Requirements</span></span>  
 <span data-ttu-id="1136a-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1136a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1136a-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1136a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1136a-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1136a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1136a-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1136a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1136a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1136a-132">See Also</span></span>  
 [<span data-ttu-id="1136a-133">Método CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="1136a-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="1136a-134">Método EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="1136a-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="1136a-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="1136a-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1136a-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="1136a-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1136a-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="1136a-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1136a-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="1136a-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="1136a-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="1136a-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="1136a-140">Invocação de plataforma examinar mais detalhadamente</span><span class="sxs-lookup"><span data-stu-id="1136a-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
