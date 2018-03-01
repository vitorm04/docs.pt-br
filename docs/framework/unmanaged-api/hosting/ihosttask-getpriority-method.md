---
title: "Método IHostTask::GetPriority"
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
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 468a2e29ed3c031889fdc5df3d4defa6506d8fcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="30f42-102">Método IHostTask::GetPriority</span><span class="sxs-lookup"><span data-stu-id="30f42-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="30f42-103">Obtém o nível de prioridade de thread da tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="30f42-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30f42-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30f42-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30f42-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="30f42-106">[out] Um ponteiro para um inteiro que indica o nível de prioridade de thread da tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="30f42-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30f42-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="30f42-107">Return Value</span></span>  
  
|<span data-ttu-id="30f42-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30f42-108">HRESULT</span></span>|<span data-ttu-id="30f42-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="30f42-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30f42-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="30f42-110">S_OK</span></span>|<span data-ttu-id="30f42-111">`GetPriority`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="30f42-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="30f42-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30f42-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30f42-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="30f42-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30f42-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30f42-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30f42-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="30f42-115">The call timed out.</span></span>|  
|<span data-ttu-id="30f42-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30f42-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30f42-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="30f42-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30f42-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30f42-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30f42-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="30f42-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30f42-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30f42-120">E_FAIL</span></span>|<span data-ttu-id="30f42-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="30f42-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30f42-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="30f42-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30f42-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="30f42-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30f42-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="30f42-124">Remarks</span></span>  
 <span data-ttu-id="30f42-125">Valores de nível de prioridade de thread são definidos pelo Win32 `SetThreadPriority` função.</span><span class="sxs-lookup"><span data-stu-id="30f42-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30f42-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30f42-126">Requirements</span></span>  
 <span data-ttu-id="30f42-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30f42-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30f42-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30f42-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30f42-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="30f42-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30f42-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30f42-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f42-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30f42-131">See Also</span></span>  
 [<span data-ttu-id="30f42-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="30f42-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="30f42-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="30f42-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="30f42-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="30f42-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="30f42-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="30f42-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
