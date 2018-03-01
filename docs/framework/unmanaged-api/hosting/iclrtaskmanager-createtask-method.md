---
title: "Método ICLRTaskManager::CreateTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9e78db6e43397709f913f8f79a617221f98db87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="7abd6-102">Método ICLRTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="7abd6-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="7abd6-103">Solicita explicitamente que o common language runtime (CLR) crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="7abd6-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7abd6-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7abd6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7abd6-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="7abd6-106">[out] Um ponteiro para o endereço de um recém-criado [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), ou nulo, se a tarefa não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="7abd6-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7abd6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7abd6-107">Return Value</span></span>  
  
|<span data-ttu-id="7abd6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7abd6-108">HRESULT</span></span>|<span data-ttu-id="7abd6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7abd6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7abd6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7abd6-110">S_OK</span></span>|<span data-ttu-id="7abd6-111">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7abd6-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="7abd6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7abd6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7abd6-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7abd6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7abd6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7abd6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7abd6-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7abd6-115">The call timed out.</span></span>|  
|<span data-ttu-id="7abd6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7abd6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7abd6-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7abd6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7abd6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7abd6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7abd6-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7abd6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7abd6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7abd6-120">E_FAIL</span></span>|<span data-ttu-id="7abd6-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7abd6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7abd6-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7abd6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7abd6-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7abd6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7abd6-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7abd6-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7abd6-125">Não há memória suficiente está disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="7abd6-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7abd6-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="7abd6-126">Remarks</span></span>  
 <span data-ttu-id="7abd6-127">O CLR cria uma nova tarefa automaticamente na inicialização, quando o código do usuário cria um thread usando tipos no <xref:System.Threading> namespace, ou quando o tamanho do pool de threads é aumentado.</span><span class="sxs-lookup"><span data-stu-id="7abd6-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="7abd6-128">Ele também cria tarefas quando o código não gerenciado faz uma chamada para uma função gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7abd6-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="7abd6-129">`CreateTask`permite que o host fazer uma solicitação explícita do CLR cria uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="7abd6-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="7abd6-130">Por exemplo, o host pode chamar esse método para pré-inicializar estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="7abd6-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7abd6-131">A nova tarefa será retornada em um estado suspenso e permanecerá suspensa até que o host explicitamente chama [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="7abd6-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abd6-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7abd6-132">Requirements</span></span>  
 <span data-ttu-id="7abd6-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abd6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abd6-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7abd6-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7abd6-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7abd6-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7abd6-136">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abd6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abd6-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7abd6-137">See Also</span></span>  
 [<span data-ttu-id="7abd6-138">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7abd6-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7abd6-139">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7abd6-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7abd6-140">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7abd6-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7abd6-141">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7abd6-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
