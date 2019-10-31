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
ms.openlocfilehash: dda68041dbf4efa82a35c48702d83aa231462fef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121383"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="03bfd-102">Método IHostTask::Join</span><span class="sxs-lookup"><span data-stu-id="03bfd-102">IHostTask::Join Method</span></span>
<span data-ttu-id="03bfd-103">Bloqueia a tarefa de chamada até que a tarefa representada pela instância [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) atual seja concluída, o intervalo de tempo especificado decorre ou [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="03bfd-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03bfd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03bfd-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03bfd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03bfd-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="03bfd-106">no O intervalo de tempo, em milissegundos, para aguardar até que a tarefa seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="03bfd-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="03bfd-107">Se esse intervalo expirar antes da tarefa ser encerrada, a tarefa de chamada desbloqueará.</span><span class="sxs-lookup"><span data-stu-id="03bfd-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="03bfd-108">no Um dos valores de [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="03bfd-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="03bfd-109">Um valor de WAIT_ALERTABLE instrui o host a ativar a tarefa se `Alert` for chamado antes que `milliseconds` decorra.</span><span class="sxs-lookup"><span data-stu-id="03bfd-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03bfd-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="03bfd-110">Return Value</span></span>  
  
|<span data-ttu-id="03bfd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03bfd-111">HRESULT</span></span>|<span data-ttu-id="03bfd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="03bfd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03bfd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="03bfd-113">S_OK</span></span>|<span data-ttu-id="03bfd-114">`Join` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="03bfd-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="03bfd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03bfd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03bfd-116">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="03bfd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03bfd-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03bfd-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03bfd-118">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="03bfd-118">The call timed out.</span></span>|  
|<span data-ttu-id="03bfd-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03bfd-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03bfd-120">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="03bfd-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03bfd-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03bfd-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03bfd-122">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava aguardando, ou a instância de `IHostTask` atual não está associada a uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="03bfd-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="03bfd-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03bfd-123">E_FAIL</span></span>|<span data-ttu-id="03bfd-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="03bfd-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03bfd-125">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="03bfd-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03bfd-126">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="03bfd-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03bfd-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03bfd-127">Requirements</span></span>  
 <span data-ttu-id="03bfd-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03bfd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03bfd-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="03bfd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03bfd-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03bfd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03bfd-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03bfd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03bfd-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03bfd-132">See also</span></span>

- [<span data-ttu-id="03bfd-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="03bfd-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="03bfd-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="03bfd-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="03bfd-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="03bfd-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="03bfd-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="03bfd-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="03bfd-137">Enumeração WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="03bfd-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
