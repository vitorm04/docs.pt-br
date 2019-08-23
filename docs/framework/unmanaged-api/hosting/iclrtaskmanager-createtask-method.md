---
title: Método ICLRTaskManager::CreateTask
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a89ea76d78431ae8833602588379d5150e473710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938313"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="e08b9-102">Método ICLRTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="e08b9-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="e08b9-103">Solicitações explicitamente que o Common Language Runtime (CLR) cria uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="e08b9-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e08b9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e08b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e08b9-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="e08b9-106">fora Um ponteiro para o endereço de um [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)recém-criado, ou NULL, se a tarefa não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="e08b9-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e08b9-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e08b9-107">Return Value</span></span>  
  
|<span data-ttu-id="e08b9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e08b9-108">HRESULT</span></span>|<span data-ttu-id="e08b9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e08b9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e08b9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e08b9-110">S_OK</span></span>|<span data-ttu-id="e08b9-111">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="e08b9-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="e08b9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e08b9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e08b9-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e08b9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e08b9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e08b9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e08b9-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e08b9-115">The call timed out.</span></span>|  
|<span data-ttu-id="e08b9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e08b9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e08b9-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e08b9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e08b9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e08b9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e08b9-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e08b9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e08b9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e08b9-120">E_FAIL</span></span>|<span data-ttu-id="e08b9-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e08b9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e08b9-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e08b9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e08b9-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e08b9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e08b9-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e08b9-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e08b9-125">Não há memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="e08b9-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e08b9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e08b9-126">Remarks</span></span>  
 <span data-ttu-id="e08b9-127">O CLR cria uma nova tarefa automaticamente na inicialização, quando o código do usuário cria um thread usando tipos no <xref:System.Threading> namespace ou quando o tamanho do pool de threads é aumentado.</span><span class="sxs-lookup"><span data-stu-id="e08b9-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="e08b9-128">Ele também cria tarefas quando o código não gerenciado faz uma chamada para uma função gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e08b9-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="e08b9-129">`CreateTask`permite que o host faça uma solicitação explícita de que o CLR crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="e08b9-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="e08b9-130">Por exemplo, o host pode invocar esse método para inicializar as estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="e08b9-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e08b9-131">A nova tarefa é retornada em um estado suspenso e permanece suspensa até que o host chame explicitamente [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="e08b9-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e08b9-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e08b9-132">Requirements</span></span>  
 <span data-ttu-id="e08b9-133">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e08b9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e08b9-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e08b9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e08b9-135">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e08b9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e08b9-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e08b9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e08b9-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e08b9-137">See also</span></span>

- [<span data-ttu-id="e08b9-138">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="e08b9-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e08b9-139">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="e08b9-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e08b9-140">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="e08b9-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e08b9-141">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="e08b9-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
