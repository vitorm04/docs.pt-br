---
title: "Método IHostTaskManager::GetCurrentTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3ba8cbaac28df49a2df70492c1a292ee8cd287e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="95e0c-102">Método IHostTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="95e0c-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="95e0c-103">Obtém um ponteiro de interface para a tarefa que está em execução no thread de sistema operacional do qual esta chamada é feita.</span><span class="sxs-lookup"><span data-stu-id="95e0c-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e0c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95e0c-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95e0c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95e0c-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="95e0c-106">[out] Um ponteiro para o endereço de um [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que representa a tarefa em execução no momento, ou nulo, se nenhuma tarefa estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="95e0c-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95e0c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="95e0c-107">Return Value</span></span>  
  
|<span data-ttu-id="95e0c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95e0c-108">HRESULT</span></span>|<span data-ttu-id="95e0c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="95e0c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95e0c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="95e0c-110">S_OK</span></span>|<span data-ttu-id="95e0c-111">`GetCurrentTask`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="95e0c-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="95e0c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95e0c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95e0c-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="95e0c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95e0c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95e0c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95e0c-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="95e0c-115">The call timed out.</span></span>|  
|<span data-ttu-id="95e0c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95e0c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95e0c-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="95e0c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95e0c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95e0c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95e0c-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="95e0c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95e0c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95e0c-120">E_FAIL</span></span>|<span data-ttu-id="95e0c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="95e0c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95e0c-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="95e0c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95e0c-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="95e0c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95e0c-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="95e0c-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="95e0c-125">`GetCurrentTask`foi chamado em um thread de sistema operacional fora do controle do host.</span><span class="sxs-lookup"><span data-stu-id="95e0c-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95e0c-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="95e0c-126">Remarks</span></span>  
 <span data-ttu-id="95e0c-127">O host também pode definir o `pTask` parâmetro como null para impedir que uma tarefa que não foram iniciadas inserindo o CLR.</span><span class="sxs-lookup"><span data-stu-id="95e0c-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95e0c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95e0c-128">Requirements</span></span>  
 <span data-ttu-id="95e0c-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95e0c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e0c-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95e0c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95e0c-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="95e0c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95e0c-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e0c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e0c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95e0c-133">See Also</span></span>  
 [<span data-ttu-id="95e0c-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="95e0c-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="95e0c-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="95e0c-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="95e0c-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="95e0c-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="95e0c-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="95e0c-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
