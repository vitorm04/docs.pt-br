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
ms.openlocfilehash: 9829f57da911b43626516284e4858adc4139a3ca
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762846"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="98c05-102">Método ICLRTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="98c05-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="98c05-103">Solicitações explicitamente que o Common Language Runtime (CLR) cria uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="98c05-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98c05-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98c05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98c05-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="98c05-106">fora Um ponteiro para o endereço de um [ICLRTask](iclrtask-interface.md)recém-criado, ou NULL, se a tarefa não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="98c05-106">[out] A pointer to the address of a newly created [ICLRTask](iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98c05-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="98c05-107">Return Value</span></span>  
  
|<span data-ttu-id="98c05-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98c05-108">HRESULT</span></span>|<span data-ttu-id="98c05-109">Description</span><span class="sxs-lookup"><span data-stu-id="98c05-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98c05-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="98c05-110">S_OK</span></span>|<span data-ttu-id="98c05-111">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="98c05-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="98c05-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98c05-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98c05-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="98c05-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98c05-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98c05-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98c05-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="98c05-115">The call timed out.</span></span>|  
|<span data-ttu-id="98c05-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98c05-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98c05-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="98c05-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98c05-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98c05-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98c05-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="98c05-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98c05-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98c05-120">E_FAIL</span></span>|<span data-ttu-id="98c05-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="98c05-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98c05-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="98c05-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98c05-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="98c05-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98c05-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="98c05-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="98c05-125">Não há memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="98c05-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98c05-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="98c05-126">Remarks</span></span>  
 <span data-ttu-id="98c05-127">O CLR cria uma nova tarefa automaticamente na inicialização, quando o código do usuário cria um thread usando tipos no <xref:System.Threading> namespace ou quando o tamanho do pool de threads é aumentado.</span><span class="sxs-lookup"><span data-stu-id="98c05-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="98c05-128">Ele também cria tarefas quando o código não gerenciado faz uma chamada para uma função gerenciada.</span><span class="sxs-lookup"><span data-stu-id="98c05-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="98c05-129">`CreateTask`permite que o host faça uma solicitação explícita de que o CLR crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="98c05-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="98c05-130">Por exemplo, o host pode invocar esse método para inicializar as estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="98c05-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="98c05-131">A nova tarefa é retornada em um estado suspenso e permanece suspensa até que o host chame explicitamente [IHostTask:: Start](ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="98c05-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98c05-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98c05-132">Requirements</span></span>  
 <span data-ttu-id="98c05-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98c05-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98c05-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98c05-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98c05-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="98c05-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98c05-136">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98c05-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c05-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="98c05-137">See also</span></span>

- [<span data-ttu-id="98c05-138">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="98c05-138">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="98c05-139">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="98c05-139">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="98c05-140">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="98c05-140">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="98c05-141">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="98c05-141">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
