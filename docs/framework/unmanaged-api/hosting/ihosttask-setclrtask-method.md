---
title: "Método IHostTask::SetCLRTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetCLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54706b1c3a6ea1864137e2eca135fa6bd883b345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="c2d8c-102">Método IHostTask::SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="c2d8c-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="c2d8c-103">Associa um `ICLRTask` instância com a atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d8c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2d8c-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2d8c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2d8c-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="c2d8c-106">[in] Um ponteiro de interface para o `ICLRTask` instância a ser associado com a atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2d8c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c2d8c-107">Return Value</span></span>  
  
|<span data-ttu-id="c2d8c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2d8c-108">HRESULT</span></span>|<span data-ttu-id="c2d8c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2d8c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2d8c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2d8c-110">S_OK</span></span>|<span data-ttu-id="c2d8c-111">`SetCLRTask`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="c2d8c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2d8c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2d8c-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2d8c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2d8c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2d8c-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-115">The call timed out.</span></span>|  
|<span data-ttu-id="c2d8c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2d8c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2d8c-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2d8c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2d8c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2d8c-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2d8c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2d8c-120">E_FAIL</span></span>|<span data-ttu-id="c2d8c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2d8c-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2d8c-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2d8c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2d8c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2d8c-124">Remarks</span></span>  
 <span data-ttu-id="c2d8c-125">O CLR chama `SetCLRTask` para associar um `ICLRTask` instância com a atual `IHostTask` instância, que foi criada por uma chamada para [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="c2d8c-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d8c-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2d8c-126">Requirements</span></span>  
 <span data-ttu-id="c2d8c-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d8c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d8c-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2d8c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2d8c-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c2d8c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2d8c-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d8c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d8c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2d8c-131">See Also</span></span>  
 [<span data-ttu-id="c2d8c-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="c2d8c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c2d8c-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="c2d8c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c2d8c-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="c2d8c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c2d8c-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="c2d8c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
