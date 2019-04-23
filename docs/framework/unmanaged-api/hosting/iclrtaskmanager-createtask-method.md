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
ms.openlocfilehash: 8833daa9cd385a1a76c5b706f15a76bb15139b84
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079664"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="adc1d-102">Método ICLRTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="adc1d-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="adc1d-103">Solicita explicitamente que o common language runtime (CLR) crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="adc1d-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc1d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adc1d-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adc1d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="adc1d-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="adc1d-106">[out] Um ponteiro para o endereço de um recém-criado [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), ou nulo, se a tarefa não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="adc1d-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adc1d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="adc1d-107">Return Value</span></span>  
  
|<span data-ttu-id="adc1d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="adc1d-108">HRESULT</span></span>|<span data-ttu-id="adc1d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="adc1d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adc1d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="adc1d-110">S_OK</span></span>|<span data-ttu-id="adc1d-111">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="adc1d-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="adc1d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="adc1d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="adc1d-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="adc1d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="adc1d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="adc1d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="adc1d-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="adc1d-115">The call timed out.</span></span>|  
|<span data-ttu-id="adc1d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="adc1d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="adc1d-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="adc1d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="adc1d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="adc1d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="adc1d-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="adc1d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="adc1d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="adc1d-120">E_FAIL</span></span>|<span data-ttu-id="adc1d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="adc1d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="adc1d-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="adc1d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="adc1d-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="adc1d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="adc1d-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="adc1d-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="adc1d-125">Não há memória suficiente está disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="adc1d-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc1d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="adc1d-126">Remarks</span></span>  
 <span data-ttu-id="adc1d-127">O CLR cria uma nova tarefa automaticamente na inicialização, quando o código do usuário cria um thread usando tipos no <xref:System.Threading> namespace, ou quando o tamanho do pool de threads é aumentado.</span><span class="sxs-lookup"><span data-stu-id="adc1d-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="adc1d-128">Ele também cria tarefas quando o código não gerenciado faz uma chamada para uma função gerenciada.</span><span class="sxs-lookup"><span data-stu-id="adc1d-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="adc1d-129">`CreateTask` permite que o host fazer uma solicitação explícita, o CLR cria uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="adc1d-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="adc1d-130">Por exemplo, o host pode chamar esse método para preinitialize estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="adc1d-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="adc1d-131">A nova tarefa é retornada em um estado suspenso e permanece suspensa até que o host chama explicitamente [ihosttask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="adc1d-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adc1d-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="adc1d-132">Requirements</span></span>  
 <span data-ttu-id="adc1d-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc1d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc1d-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="adc1d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adc1d-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="adc1d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adc1d-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc1d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc1d-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adc1d-137">See also</span></span>

- [<span data-ttu-id="adc1d-138">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="adc1d-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="adc1d-139">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="adc1d-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="adc1d-140">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="adc1d-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="adc1d-141">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="adc1d-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
