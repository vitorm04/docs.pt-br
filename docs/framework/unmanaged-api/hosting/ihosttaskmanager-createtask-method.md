---
title: Método IHostTaskManager::CreateTask
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33cffb086609432f5207310fc565bd34cccd7642
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698637"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="6e230-102">Método IHostTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="6e230-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="6e230-103">Solicita que o host, crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="6e230-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e230-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e230-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e230-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e230-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="6e230-106">[in] O tamanho solicitado, em bytes, da pilha solicitada ou 0 (zero) para o tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="6e230-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="6e230-107">[in] Um ponteiro para a função a tarefa é executar.</span><span class="sxs-lookup"><span data-stu-id="6e230-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="6e230-108">[in] Um ponteiro para os dados do usuário a serem passados para a função ou nulo se a função não usa nenhum parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6e230-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="6e230-109">[out] Um ponteiro para o endereço de um [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância criada pelo host ou nulo se a tarefa não pode ser criada.</span><span class="sxs-lookup"><span data-stu-id="6e230-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="6e230-110">A tarefa permanece em um estado suspenso até que ela é iniciada explicitamente por uma chamada para [ihosttask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e230-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e230-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6e230-111">Return Value</span></span>  
  
|<span data-ttu-id="6e230-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e230-112">HRESULT</span></span>|<span data-ttu-id="6e230-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e230-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e230-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e230-114">S_OK</span></span>|<span data-ttu-id="6e230-115">`CreateTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6e230-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="6e230-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e230-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e230-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6e230-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e230-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e230-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e230-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6e230-119">The call timed out.</span></span>|  
|<span data-ttu-id="6e230-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e230-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e230-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6e230-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e230-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e230-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e230-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="6e230-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e230-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e230-124">E_FAIL</span></span>|<span data-ttu-id="6e230-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6e230-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e230-126">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="6e230-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e230-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6e230-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6e230-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6e230-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6e230-129">Não havia memória suficiente disponível para criar a tarefa solicitada.</span><span class="sxs-lookup"><span data-stu-id="6e230-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e230-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e230-130">Remarks</span></span>  
 <span data-ttu-id="6e230-131">O CLR chama `CreateTask` para solicitar que o host, crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="6e230-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="6e230-132">O host retorna um ponteiro de interface para um `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="6e230-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="6e230-133">A tarefa retornada deve permanecer suspensa até que ela é iniciada explicitamente por uma chamada para `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="6e230-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e230-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e230-134">Requirements</span></span>  
 <span data-ttu-id="6e230-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e230-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e230-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e230-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e230-137">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6e230-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e230-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e230-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e230-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e230-139">See also</span></span>
- [<span data-ttu-id="6e230-140">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="6e230-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6e230-141">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="6e230-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6e230-142">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="6e230-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6e230-143">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="6e230-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
