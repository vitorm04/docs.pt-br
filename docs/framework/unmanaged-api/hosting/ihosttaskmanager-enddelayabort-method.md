---
title: "Método IHostTaskManager::EndDelayAbort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EndDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45148c506e2f6073dc175abe4397fad2172b355e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="19bfa-102">Método IHostTaskManager::EndDelayAbort</span><span class="sxs-lookup"><span data-stu-id="19bfa-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="19bfa-103">Notifica o host que o código gerenciado está saindo do período em que a tarefa atual não deve ser interrompida, após uma chamada anterior para [Begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="19bfa-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19bfa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19bfa-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="19bfa-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="19bfa-105">Return Value</span></span>  
  
|<span data-ttu-id="19bfa-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19bfa-106">HRESULT</span></span>|<span data-ttu-id="19bfa-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="19bfa-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19bfa-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="19bfa-108">S_OK</span></span>|<span data-ttu-id="19bfa-109">`EndDelayAbort`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="19bfa-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="19bfa-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19bfa-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19bfa-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="19bfa-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19bfa-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19bfa-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19bfa-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="19bfa-113">The call timed out.</span></span>|  
|<span data-ttu-id="19bfa-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19bfa-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19bfa-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="19bfa-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19bfa-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19bfa-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19bfa-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="19bfa-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19bfa-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19bfa-118">E_FAIL</span></span>|<span data-ttu-id="19bfa-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="19bfa-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19bfa-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="19bfa-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19bfa-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="19bfa-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="19bfa-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="19bfa-122">E_UNEXPECTED</span></span>|<span data-ttu-id="19bfa-123">`EndDelayAbort`foi chamado sem uma chamada correspondente para `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="19bfa-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19bfa-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="19bfa-124">Remarks</span></span>  
 <span data-ttu-id="19bfa-125">O CLR faz uma chamada correspondente para `BeginDelayAbort` da tarefa atual antes de chamar `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="19bfa-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="19bfa-126">Na ausência de tal chamada correspondente, a implementação do host de [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) deve retornar E_UNEXPECTED de `EndDelayAbort`e não deve tomar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="19bfa-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19bfa-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19bfa-127">Requirements</span></span>  
 <span data-ttu-id="19bfa-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19bfa-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19bfa-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="19bfa-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19bfa-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="19bfa-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19bfa-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19bfa-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bfa-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19bfa-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="19bfa-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="19bfa-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="19bfa-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="19bfa-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="19bfa-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="19bfa-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="19bfa-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="19bfa-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
