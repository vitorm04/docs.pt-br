---
title: Método IHostTask::GetPriority
ms.date: 03/30/2017
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
ms.openlocfilehash: 6c33fa6d2e6cb09f013c5334461e61235db549f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121412"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="b60ff-102">Método IHostTask::GetPriority</span><span class="sxs-lookup"><span data-stu-id="b60ff-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="b60ff-103">Obtém o nível de prioridade de thread da tarefa representada pela instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="b60ff-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b60ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b60ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b60ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b60ff-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="b60ff-106">fora Um ponteiro para um inteiro que indica o nível de prioridade de thread da tarefa representada pela instância de `IHostTask` atual.</span><span class="sxs-lookup"><span data-stu-id="b60ff-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b60ff-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b60ff-107">Return Value</span></span>  
  
|<span data-ttu-id="b60ff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b60ff-108">HRESULT</span></span>|<span data-ttu-id="b60ff-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b60ff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b60ff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b60ff-110">S_OK</span></span>|<span data-ttu-id="b60ff-111">`GetPriority` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b60ff-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="b60ff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b60ff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b60ff-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b60ff-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b60ff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b60ff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b60ff-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b60ff-115">The call timed out.</span></span>|  
|<span data-ttu-id="b60ff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b60ff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b60ff-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b60ff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b60ff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b60ff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b60ff-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b60ff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b60ff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b60ff-120">E_FAIL</span></span>|<span data-ttu-id="b60ff-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b60ff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b60ff-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b60ff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b60ff-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b60ff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b60ff-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="b60ff-124">Remarks</span></span>  
 <span data-ttu-id="b60ff-125">Os valores de nível de prioridade de thread são definidos pela função de `SetThreadPriority` do Win32.</span><span class="sxs-lookup"><span data-stu-id="b60ff-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b60ff-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b60ff-126">Requirements</span></span>  
 <span data-ttu-id="b60ff-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b60ff-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b60ff-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b60ff-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b60ff-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b60ff-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b60ff-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b60ff-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b60ff-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b60ff-131">See also</span></span>

- [<span data-ttu-id="b60ff-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b60ff-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b60ff-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b60ff-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b60ff-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="b60ff-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b60ff-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b60ff-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
