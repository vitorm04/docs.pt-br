---
title: Método ICLRTask::YieldTask
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
ms.openlocfilehash: 43f2048c8ab85fa7e94f73aad430400ad4c8352f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124590"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="81468-102">Método ICLRTask::YieldTask</span><span class="sxs-lookup"><span data-stu-id="81468-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="81468-103">Solicita que o Common Language Runtime (CLR) separe a tarefa que a instância [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual representa e disponibilize o tempo do processador para outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="81468-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81468-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81468-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="81468-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="81468-105">Return Value</span></span>  
  
|<span data-ttu-id="81468-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81468-106">HRESULT</span></span>|<span data-ttu-id="81468-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="81468-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81468-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="81468-108">S_OK</span></span>|<span data-ttu-id="81468-109">`YieldTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="81468-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="81468-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81468-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81468-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="81468-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81468-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81468-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81468-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="81468-113">The call timed out.</span></span>|  
|<span data-ttu-id="81468-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81468-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81468-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="81468-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81468-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81468-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81468-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="81468-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81468-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81468-118">E_FAIL</span></span>|<span data-ttu-id="81468-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="81468-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81468-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="81468-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81468-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="81468-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81468-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="81468-122">Remarks</span></span>  
 <span data-ttu-id="81468-123">Um host chama `YieldTask` para solicitar recursos do processador para outras tarefas ou processos.</span><span class="sxs-lookup"><span data-stu-id="81468-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="81468-124">Esse método destina-se principalmente a permitir o código de execução longa para desistir do tempo de CPU.</span><span class="sxs-lookup"><span data-stu-id="81468-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="81468-125">O tempo de execução tenta colocar a tarefa que a instância de `ICLRTask` atual representa em um estado em que pode gerar tempo de processamento, mas não garante o sucesso.</span><span class="sxs-lookup"><span data-stu-id="81468-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81468-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81468-126">Requirements</span></span>  
 <span data-ttu-id="81468-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81468-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81468-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81468-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81468-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81468-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81468-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81468-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81468-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81468-131">See also</span></span>

- [<span data-ttu-id="81468-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="81468-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="81468-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="81468-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="81468-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="81468-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="81468-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="81468-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
