---
title: "Método ICLRTaskManager::GetCurrentTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 04d12e3ff17cc422121e62f08a77f0271ed78346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="9f008-102">Método ICLRTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="9f008-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="9f008-103">Obtém o [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância que está em execução no thread do sistema operacional que originou a chamada do método.</span><span class="sxs-lookup"><span data-stu-id="9f008-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f008-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f008-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f008-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f008-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="9f008-106">[out] Um ponteiro para o endereço de um `ICLRTask` instância que está em execução no thread de sistema operacional que originou a chamada, ou nulo se nenhuma tarefa estiver em execução neste thread.</span><span class="sxs-lookup"><span data-stu-id="9f008-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f008-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9f008-107">Return Value</span></span>  
  
|<span data-ttu-id="9f008-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f008-108">HRESULT</span></span>|<span data-ttu-id="9f008-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f008-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f008-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f008-110">S_OK</span></span>|<span data-ttu-id="9f008-111">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9f008-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="9f008-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f008-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f008-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9f008-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9f008-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f008-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9f008-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="9f008-115">The call timed out.</span></span>|  
|<span data-ttu-id="9f008-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9f008-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9f008-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9f008-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9f008-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9f008-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9f008-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="9f008-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9f008-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9f008-120">E_FAIL</span></span>|<span data-ttu-id="9f008-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9f008-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9f008-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="9f008-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9f008-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9f008-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f008-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f008-124">Remarks</span></span>  
 <span data-ttu-id="9f008-125">O `ICLRTask` instância em que o `ppTask` parâmetro aponta para representa a tarefa em execução no momento para o CLR.</span><span class="sxs-lookup"><span data-stu-id="9f008-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="9f008-126">O `ICLRTask` instância está associada um correspondente [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que representa a tarefa para o host.</span><span class="sxs-lookup"><span data-stu-id="9f008-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f008-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f008-127">Requirements</span></span>  
 <span data-ttu-id="9f008-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f008-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f008-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9f008-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f008-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9f008-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f008-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f008-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f008-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f008-132">See Also</span></span>  
 [<span data-ttu-id="9f008-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="9f008-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9f008-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="9f008-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9f008-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="9f008-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9f008-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="9f008-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
