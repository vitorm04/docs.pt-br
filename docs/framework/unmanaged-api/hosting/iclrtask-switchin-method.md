---
title: Método ICLRTask::SwitchIn
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
ms.openlocfilehash: d8f57af459d1bb3f338cfbfcbb29f69f533ea927
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762923"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="82648-102">Método ICLRTask::SwitchIn</span><span class="sxs-lookup"><span data-stu-id="82648-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="82648-103">Notifica o Common Language Runtime (CLR) que a tarefa que a instância [ICLRTask](iclrtask-interface.md) atual representa agora está em um estado operável.</span><span class="sxs-lookup"><span data-stu-id="82648-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82648-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82648-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82648-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82648-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="82648-106">no Um identificador para o thread físico no qual a tarefa representada pela instância atual `ICLRTask` está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="82648-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82648-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="82648-107">Return Value</span></span>  
  
|<span data-ttu-id="82648-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82648-108">HRESULT</span></span>|<span data-ttu-id="82648-109">Description</span><span class="sxs-lookup"><span data-stu-id="82648-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82648-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="82648-110">S_OK</span></span>|<span data-ttu-id="82648-111">`SwitchIn`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="82648-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="82648-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82648-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82648-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="82648-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82648-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82648-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82648-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="82648-115">The call timed out.</span></span>|  
|<span data-ttu-id="82648-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82648-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82648-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="82648-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82648-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82648-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82648-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="82648-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82648-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82648-120">E_FAIL</span></span>|<span data-ttu-id="82648-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="82648-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82648-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="82648-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82648-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="82648-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="82648-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="82648-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="82648-125">`SwitchIn`foi chamado sem uma chamada anterior para o [método SwitchOut](iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="82648-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82648-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="82648-126">Remarks</span></span>  
 <span data-ttu-id="82648-127">O `threadHandle` parâmetro representa um identificador para o thread do sistema operacional no qual a tarefa representada pela instância atual foi `ICLRTask` agendada.</span><span class="sxs-lookup"><span data-stu-id="82648-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="82648-128">Se a representação tiver ocorrido neste thread, você deverá chamar [IHostSecurityManager:: RevertToSelf](ihostsecuritymanager-reverttoself-method.md) antes de alternar para a tarefa.</span><span class="sxs-lookup"><span data-stu-id="82648-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82648-129">Uma chamada para `SwitchIn` sem uma chamada anterior para `SwitchOut` falha com um valor HRESULT de HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="82648-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82648-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82648-130">Requirements</span></span>  
 <span data-ttu-id="82648-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82648-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82648-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="82648-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82648-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="82648-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82648-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82648-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82648-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="82648-135">See also</span></span>

- [<span data-ttu-id="82648-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="82648-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="82648-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="82648-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="82648-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="82648-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="82648-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="82648-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
