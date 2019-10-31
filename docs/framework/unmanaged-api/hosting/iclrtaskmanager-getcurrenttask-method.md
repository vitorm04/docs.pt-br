---
title: Método ICLRTaskManager::GetCurrentTask
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: a57610d1b41d80d54a245b9744aafd78a1e88177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195903"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="08ffc-102">Método ICLRTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="08ffc-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="08ffc-103">Obtém a instância [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) que está em execução no momento no thread do sistema operacional do qual a chamada do método foi originada.</span><span class="sxs-lookup"><span data-stu-id="08ffc-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08ffc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08ffc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08ffc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08ffc-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="08ffc-106">fora Um ponteiro para o endereço de uma instância de `ICLRTask` que está atualmente em execução no thread do sistema operacional do qual a chamada foi originada, ou nula se nenhuma tarefa estiver em execução no momento nesse thread.</span><span class="sxs-lookup"><span data-stu-id="08ffc-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08ffc-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="08ffc-107">Return Value</span></span>  
  
|<span data-ttu-id="08ffc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08ffc-108">HRESULT</span></span>|<span data-ttu-id="08ffc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="08ffc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08ffc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="08ffc-110">S_OK</span></span>|<span data-ttu-id="08ffc-111">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="08ffc-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="08ffc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08ffc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08ffc-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="08ffc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08ffc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08ffc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08ffc-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="08ffc-115">The call timed out.</span></span>|  
|<span data-ttu-id="08ffc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08ffc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08ffc-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="08ffc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08ffc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08ffc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08ffc-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="08ffc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08ffc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08ffc-120">E_FAIL</span></span>|<span data-ttu-id="08ffc-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="08ffc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08ffc-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="08ffc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08ffc-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="08ffc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08ffc-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="08ffc-124">Remarks</span></span>  
 <span data-ttu-id="08ffc-125">A instância de `ICLRTask` que o parâmetro `ppTask` aponta para representar a tarefa em execução no momento para o CLR.</span><span class="sxs-lookup"><span data-stu-id="08ffc-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="08ffc-126">A instância de `ICLRTask` está associada a uma instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) correspondente que representa a tarefa para o host.</span><span class="sxs-lookup"><span data-stu-id="08ffc-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08ffc-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08ffc-127">Requirements</span></span>  
 <span data-ttu-id="08ffc-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08ffc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08ffc-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="08ffc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08ffc-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08ffc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08ffc-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08ffc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ffc-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08ffc-132">See also</span></span>

- [<span data-ttu-id="08ffc-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="08ffc-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="08ffc-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="08ffc-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="08ffc-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="08ffc-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="08ffc-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="08ffc-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
