---
title: Método IHostTask::SetCLRTask
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: bbb563a304e3ff7cdba3dfe7e394da9cf138ff10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121363"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="b7a0c-102">Método IHostTask::SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="b7a0c-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="b7a0c-103">Associa uma instância de `ICLRTask` com a instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a0c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7a0c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7a0c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7a0c-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="b7a0c-106">no Um ponteiro de interface para a instância de `ICLRTask` a ser associada à instância de `IHostTask` atual.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7a0c-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b7a0c-107">Return Value</span></span>  
  
|<span data-ttu-id="b7a0c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7a0c-108">HRESULT</span></span>|<span data-ttu-id="b7a0c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7a0c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7a0c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7a0c-110">S_OK</span></span>|<span data-ttu-id="b7a0c-111">`SetCLRTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="b7a0c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7a0c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7a0c-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7a0c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7a0c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7a0c-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-115">The call timed out.</span></span>|  
|<span data-ttu-id="b7a0c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7a0c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7a0c-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7a0c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7a0c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7a0c-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7a0c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7a0c-120">E_FAIL</span></span>|<span data-ttu-id="b7a0c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7a0c-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7a0c-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b7a0c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7a0c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7a0c-124">Remarks</span></span>  
 <span data-ttu-id="b7a0c-125">O CLR chama `SetCLRTask` para associar uma instância de `ICLRTask` com a instância de `IHostTask` atual, que foi criada por uma chamada para [IHostTaskManager:: CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="b7a0c-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a0c-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7a0c-126">Requirements</span></span>  
 <span data-ttu-id="b7a0c-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7a0c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7a0c-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b7a0c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7a0c-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b7a0c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7a0c-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7a0c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a0c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7a0c-131">See also</span></span>

- [<span data-ttu-id="b7a0c-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b7a0c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b7a0c-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b7a0c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b7a0c-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="b7a0c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b7a0c-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b7a0c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
