---
title: "Método ICLRTask::LocksHeld"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.LocksHeld
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d51fded9f2e475759f2912aea659d272ce08855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="401da-102">Método ICLRTask::LocksHeld</span><span class="sxs-lookup"><span data-stu-id="401da-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="401da-103">Obtém o número de bloqueios atualmente mantidos na tarefa.</span><span class="sxs-lookup"><span data-stu-id="401da-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="401da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="401da-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="401da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="401da-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="401da-106">[out] O número de bloqueios mantidos na tarefa no momento da chamada do método.</span><span class="sxs-lookup"><span data-stu-id="401da-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="401da-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="401da-107">Return Value</span></span>  
  
|<span data-ttu-id="401da-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="401da-108">HRESULT</span></span>|<span data-ttu-id="401da-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="401da-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="401da-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="401da-110">S_OK</span></span>|<span data-ttu-id="401da-111">`LocksHeld`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="401da-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="401da-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="401da-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="401da-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="401da-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="401da-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="401da-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="401da-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="401da-115">The call timed out.</span></span>|  
|<span data-ttu-id="401da-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="401da-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="401da-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="401da-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="401da-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="401da-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="401da-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="401da-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="401da-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="401da-120">E_FAIL</span></span>|<span data-ttu-id="401da-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="401da-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="401da-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="401da-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="401da-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="401da-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="401da-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="401da-124">Requirements</span></span>  
 <span data-ttu-id="401da-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="401da-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401da-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="401da-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="401da-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="401da-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="401da-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="401da-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401da-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="401da-129">See Also</span></span>  
 [<span data-ttu-id="401da-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="401da-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="401da-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="401da-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="401da-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="401da-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="401da-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="401da-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
