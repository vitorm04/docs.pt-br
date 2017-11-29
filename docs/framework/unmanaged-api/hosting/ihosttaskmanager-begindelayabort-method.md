---
title: "Método IHostTaskManager::BeginDelayAbort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.BeginDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17af69c533c62b6a25d498fb245dfefe162690ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="cd766-102">Método IHostTaskManager::BeginDelayAbort</span><span class="sxs-lookup"><span data-stu-id="cd766-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="cd766-103">Notifica o host que o código gerenciado está inserindo um período no qual a tarefa atual não deve ser anulada.</span><span class="sxs-lookup"><span data-stu-id="cd766-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd766-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd766-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cd766-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cd766-105">Return Value</span></span>  
  
|<span data-ttu-id="cd766-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd766-106">HRESULT</span></span>|<span data-ttu-id="cd766-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd766-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd766-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd766-108">S_OK</span></span>|<span data-ttu-id="cd766-109">`BeginDelayAbort`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="cd766-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="cd766-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd766-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd766-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="cd766-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd766-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd766-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd766-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="cd766-113">The call timed out.</span></span>|  
|<span data-ttu-id="cd766-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd766-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd766-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="cd766-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd766-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd766-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd766-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="cd766-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd766-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd766-118">E_FAIL</span></span>|<span data-ttu-id="cd766-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="cd766-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd766-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="cd766-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd766-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cd766-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cd766-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="cd766-122">E_UNEXPECTED</span></span>|<span data-ttu-id="cd766-123">`BeginDelayAbort`já foi chamado, mas a chamada correspondente para [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) ainda não foi recebida.</span><span class="sxs-lookup"><span data-stu-id="cd766-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd766-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd766-124">Remarks</span></span>  
 <span data-ttu-id="cd766-125">O host não deve cancelar a tarefa atual até `EndDelayAbort` é chamado.</span><span class="sxs-lookup"><span data-stu-id="cd766-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="cd766-126">Se outra chamada `BeginDelayAbort` é feita sem uma chamada intermediária para `EndDelayAbort`, o host deve retornar E_UNEXPECTED de `BeginDelayAbort`e não deve tomar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="cd766-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd766-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd766-127">Requirements</span></span>  
 <span data-ttu-id="cd766-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd766-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd766-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd766-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd766-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cd766-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd766-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd766-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd766-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd766-132">See Also</span></span>  
 [<span data-ttu-id="cd766-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="cd766-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cd766-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="cd766-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cd766-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="cd766-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="cd766-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="cd766-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
