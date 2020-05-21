---
title: Método ICLRTask::NeedsPriorityScheduling
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
ms.openlocfilehash: df20e98a9e88c10bac748a5acfc91adcb133da79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762980"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="f2642-102">Método ICLRTask::NeedsPriorityScheduling</span><span class="sxs-lookup"><span data-stu-id="f2642-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="f2642-103">Obtém um valor que indica se a tarefa atual, que está sendo desativada, precisa ser marcada como uma prioridade alta para reagendar.</span><span class="sxs-lookup"><span data-stu-id="f2642-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2642-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2642-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2642-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2642-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="f2642-106">[fora] `true` , se o host deve tentar reagendar a instância de tarefa atual assim que possível; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="f2642-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2642-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="f2642-107">Return Value</span></span>  
  
|<span data-ttu-id="f2642-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2642-108">HRESULT</span></span>|<span data-ttu-id="f2642-109">Description</span><span class="sxs-lookup"><span data-stu-id="f2642-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2642-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2642-110">S_OK</span></span>|<span data-ttu-id="f2642-111">`NeedsPriorityRescheduling`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2642-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="f2642-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2642-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2642-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2642-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f2642-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2642-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2642-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f2642-115">The call timed out.</span></span>|  
|<span data-ttu-id="f2642-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2642-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2642-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f2642-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2642-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2642-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2642-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="f2642-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2642-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2642-120">E_FAIL</span></span>|<span data-ttu-id="f2642-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f2642-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2642-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="f2642-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2642-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f2642-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2642-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2642-124">Remarks</span></span>  
 <span data-ttu-id="f2642-125">Em situações em que a tarefa está próxima de ser coletada pelo coletor de lixo, o CLR define o valor de `pbNeedsPriorityScheduling` como `true` , indicando reagendamento de alta prioridade.</span><span class="sxs-lookup"><span data-stu-id="f2642-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="f2642-126">Isso permite que o host reagende a tarefa rapidamente, minimizando assim o potencial de atrasos na coleta de lixo e permitindo que o host e o tempo de execução cooperam em conservar recursos de memória.</span><span class="sxs-lookup"><span data-stu-id="f2642-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2642-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2642-127">Requirements</span></span>  
 <span data-ttu-id="f2642-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2642-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2642-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f2642-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2642-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f2642-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2642-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2642-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2642-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="f2642-132">See also</span></span>

- [<span data-ttu-id="f2642-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f2642-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f2642-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f2642-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f2642-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f2642-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f2642-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f2642-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
