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
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177994"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="d31ae-102">Método IHostTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="d31ae-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="d31ae-103">Solicita que o host crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="d31ae-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d31ae-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d31ae-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d31ae-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="d31ae-106">[em] O tamanho solicitado, em bytes, da pilha solicitada, ou 0 (zero) para o tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="d31ae-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="d31ae-107">[em] Um ponteiro para a função que a tarefa deve executar.</span><span class="sxs-lookup"><span data-stu-id="d31ae-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="d31ae-108">[em] Um ponteiro para os dados do usuário a ser passado para a função, ou nulo se a função não tiver parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d31ae-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="d31ae-109">[fora] Um ponteiro para o endereço de uma instância [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) criado pelo host ou nulo se a tarefa não puder ser criada.</span><span class="sxs-lookup"><span data-stu-id="d31ae-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="d31ae-110">A tarefa permanece em um estado suspenso até que seja explicitamente iniciada por uma chamada para [IHostTask:::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="d31ae-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d31ae-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d31ae-111">Return Value</span></span>  
  
|<span data-ttu-id="d31ae-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d31ae-112">HRESULT</span></span>|<span data-ttu-id="d31ae-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d31ae-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d31ae-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d31ae-114">S_OK</span></span>|<span data-ttu-id="d31ae-115">`CreateTask`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d31ae-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="d31ae-116">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="d31ae-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d31ae-117">O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d31ae-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d31ae-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d31ae-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d31ae-119">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="d31ae-119">The call timed out.</span></span>|  
|<span data-ttu-id="d31ae-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d31ae-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d31ae-121">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="d31ae-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d31ae-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d31ae-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d31ae-123">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="d31ae-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d31ae-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d31ae-124">E_FAIL</span></span>|<span data-ttu-id="d31ae-125">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="d31ae-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d31ae-126">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d31ae-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d31ae-127">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d31ae-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d31ae-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d31ae-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d31ae-129">Não havia memória suficiente para criar a tarefa solicitada.</span><span class="sxs-lookup"><span data-stu-id="d31ae-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d31ae-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="d31ae-130">Remarks</span></span>  
 <span data-ttu-id="d31ae-131">O CLR `CreateTask` chama para solicitar que o host crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="d31ae-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="d31ae-132">O host retorna um `IHostTask` ponteiro de interface para uma instância.</span><span class="sxs-lookup"><span data-stu-id="d31ae-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="d31ae-133">A tarefa retornada deve permanecer suspensa até que seja `IHostTask::Start`explicitamente iniciada por uma chamada para .</span><span class="sxs-lookup"><span data-stu-id="d31ae-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d31ae-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d31ae-134">Requirements</span></span>  
 <span data-ttu-id="d31ae-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d31ae-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d31ae-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d31ae-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d31ae-137">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d31ae-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d31ae-138">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d31ae-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31ae-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="d31ae-139">See also</span></span>

- [<span data-ttu-id="d31ae-140">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d31ae-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d31ae-141">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d31ae-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d31ae-142">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="d31ae-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d31ae-143">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d31ae-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
