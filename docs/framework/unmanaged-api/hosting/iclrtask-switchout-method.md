---
title: Método ICLRTask::SwitchOut
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: f9c2e77013ff9e31a0a2ef3b4ca511b76ae345e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124607"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="c1b32-102">Método ICLRTask::SwitchOut</span><span class="sxs-lookup"><span data-stu-id="c1b32-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="c1b32-103">Notifica o Common Language Runtime (CLR) que a tarefa representada pela instância [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual não está mais em um estado operável.</span><span class="sxs-lookup"><span data-stu-id="c1b32-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b32-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1b32-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c1b32-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c1b32-105">Return Value</span></span>  
  
|<span data-ttu-id="c1b32-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1b32-106">HRESULT</span></span>|<span data-ttu-id="c1b32-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1b32-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1b32-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1b32-108">S_OK</span></span>|<span data-ttu-id="c1b32-109">`SwitchOut` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c1b32-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="c1b32-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1b32-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1b32-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c1b32-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1b32-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1b32-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1b32-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c1b32-113">The call timed out.</span></span>|  
|<span data-ttu-id="c1b32-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1b32-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1b32-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c1b32-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1b32-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1b32-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1b32-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="c1b32-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1b32-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1b32-118">E_FAIL</span></span>|<span data-ttu-id="c1b32-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c1b32-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1b32-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="c1b32-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1b32-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c1b32-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1b32-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1b32-122">Remarks</span></span>  
 <span data-ttu-id="c1b32-123">Um host chama `SwitchOut` para informar ao CLR que ele interrompeu temporariamente a execução da tarefa que a instância `ICLRTask` atual representa e reagendará a tarefa.</span><span class="sxs-lookup"><span data-stu-id="c1b32-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b32-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1b32-124">Requirements</span></span>  
 <span data-ttu-id="c1b32-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b32-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b32-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c1b32-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1b32-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c1b32-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1b32-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b32-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b32-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1b32-129">See also</span></span>

- [<span data-ttu-id="c1b32-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="c1b32-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c1b32-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="c1b32-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c1b32-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="c1b32-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c1b32-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="c1b32-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
