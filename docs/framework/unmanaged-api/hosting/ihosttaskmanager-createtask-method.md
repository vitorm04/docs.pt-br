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
ms.openlocfilehash: 4037ffe63d8ebfca67cbd0b3293d36be7481b1bd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501411"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="7a686-102">Método IHostTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="7a686-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="7a686-103">Solicita que o host crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="7a686-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a686-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a686-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a686-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a686-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="7a686-106">no O tamanho solicitado, em bytes, da pilha solicitada ou de 0 (zero) para o tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="7a686-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="7a686-107">no Um ponteiro para a função que a tarefa deve executar.</span><span class="sxs-lookup"><span data-stu-id="7a686-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="7a686-108">no Um ponteiro para os dados do usuário a serem passados para a função, ou NULL se a função não usar parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7a686-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="7a686-109">fora Um ponteiro para o endereço de uma instância de [IHostTask](ihosttask-interface.md) criada pelo host ou NULL se a tarefa não puder ser criada.</span><span class="sxs-lookup"><span data-stu-id="7a686-109">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="7a686-110">A tarefa permanece em um estado suspenso até que seja explicitamente iniciada por uma chamada para [IHostTask:: Start](ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="7a686-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a686-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="7a686-111">Return Value</span></span>  
  
|<span data-ttu-id="7a686-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a686-112">HRESULT</span></span>|<span data-ttu-id="7a686-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a686-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a686-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a686-114">S_OK</span></span>|<span data-ttu-id="7a686-115">`CreateTask`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7a686-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="7a686-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7a686-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7a686-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7a686-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7a686-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7a686-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7a686-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7a686-119">The call timed out.</span></span>|  
|<span data-ttu-id="7a686-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7a686-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7a686-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7a686-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7a686-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7a686-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7a686-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7a686-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7a686-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7a686-124">E_FAIL</span></span>|<span data-ttu-id="7a686-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7a686-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7a686-126">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7a686-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7a686-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7a686-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7a686-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7a686-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7a686-129">Não há memória suficiente disponível para criar a tarefa solicitada.</span><span class="sxs-lookup"><span data-stu-id="7a686-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a686-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a686-130">Remarks</span></span>  
 <span data-ttu-id="7a686-131">O CLR chama `CreateTask` para solicitar que o host crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="7a686-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="7a686-132">O host retorna um ponteiro de interface para uma `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="7a686-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="7a686-133">A tarefa retornada deve permanecer suspensa até ser explicitamente iniciada por uma chamada para `IHostTask::Start` .</span><span class="sxs-lookup"><span data-stu-id="7a686-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a686-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a686-134">Requirements</span></span>  
 <span data-ttu-id="7a686-135">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a686-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a686-136">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7a686-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a686-137">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7a686-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a686-138">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a686-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a686-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a686-139">See also</span></span>

- [<span data-ttu-id="7a686-140">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7a686-140">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7a686-141">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7a686-141">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7a686-142">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7a686-142">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7a686-143">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7a686-143">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
