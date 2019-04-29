---
title: Método IHostTask::Join
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4373fc4e8a4c414c40e8d3c5547b5998b9300348
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789513"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="00d7d-102">Método IHostTask::Join</span><span class="sxs-lookup"><span data-stu-id="00d7d-102">IHostTask::Join Method</span></span>
<span data-ttu-id="00d7d-103">Bloqueia a tarefa de chamada até que a tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância é concluída, o intervalo de tempo especificado tenha decorrido, ou [ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="00d7d-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00d7d-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00d7d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00d7d-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="00d7d-106">[in] O intervalo de tempo, em milissegundos, para aguardar a tarefa seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="00d7d-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="00d7d-107">Se esse intervalo expira antes que a tarefa termina, desbloqueia a tarefa de chamada.</span><span class="sxs-lookup"><span data-stu-id="00d7d-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="00d7d-108">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="00d7d-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="00d7d-109">Um valor de WAIT_ALERTABLE instrui o host para ativar a tarefa se `Alert` é chamado antes de `milliseconds` tenha decorrido.</span><span class="sxs-lookup"><span data-stu-id="00d7d-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00d7d-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="00d7d-110">Return Value</span></span>  
  
|<span data-ttu-id="00d7d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00d7d-111">HRESULT</span></span>|<span data-ttu-id="00d7d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="00d7d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00d7d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="00d7d-113">S_OK</span></span>|<span data-ttu-id="00d7d-114">`Join` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="00d7d-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="00d7d-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00d7d-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00d7d-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="00d7d-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="00d7d-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00d7d-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00d7d-118">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="00d7d-118">The call timed out.</span></span>|  
|<span data-ttu-id="00d7d-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00d7d-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00d7d-120">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="00d7d-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00d7d-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00d7d-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00d7d-122">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava aguardando, ou atual `IHostTask` instância não está associada uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="00d7d-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="00d7d-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00d7d-123">E_FAIL</span></span>|<span data-ttu-id="00d7d-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="00d7d-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00d7d-125">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="00d7d-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00d7d-126">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="00d7d-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00d7d-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00d7d-127">Requirements</span></span>  
 <span data-ttu-id="00d7d-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d7d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d7d-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00d7d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00d7d-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="00d7d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00d7d-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d7d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d7d-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00d7d-132">See also</span></span>

- [<span data-ttu-id="00d7d-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="00d7d-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="00d7d-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="00d7d-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="00d7d-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="00d7d-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="00d7d-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="00d7d-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="00d7d-137">Enumeração WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="00d7d-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
