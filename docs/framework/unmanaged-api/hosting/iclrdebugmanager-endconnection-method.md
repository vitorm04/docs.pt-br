---
title: Método ICLRDebugManager::EndConnection
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: 425f40da7a53aa4af1bd14964a8136add2f59f0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135212"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="199ea-102">Método ICLRDebugManager::EndConnection</span><span class="sxs-lookup"><span data-stu-id="199ea-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="199ea-103">Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="199ea-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="199ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="199ea-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="199ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="199ea-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="199ea-106">no O identificador específico do host para a conexão e a lista associada de tarefas de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="199ea-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="199ea-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="199ea-107">Return Value</span></span>  
  
|<span data-ttu-id="199ea-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="199ea-108">HRESULT</span></span>|<span data-ttu-id="199ea-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="199ea-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="199ea-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="199ea-110">S_OK</span></span>|<span data-ttu-id="199ea-111">`EndConnection` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="199ea-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="199ea-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="199ea-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="199ea-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="199ea-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="199ea-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="199ea-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="199ea-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="199ea-115">The call timed out.</span></span>|  
|<span data-ttu-id="199ea-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="199ea-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="199ea-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="199ea-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="199ea-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="199ea-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="199ea-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="199ea-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="199ea-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="199ea-120">E_FAIL</span></span>|<span data-ttu-id="199ea-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="199ea-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="199ea-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="199ea-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="199ea-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="199ea-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="199ea-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="199ea-124">E_INVALIDARG</span></span>|<span data-ttu-id="199ea-125">A [beginconnectização](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nunca foi chamada de uso de `dwConnectionId`ou `dwConnectionId` era zero.</span><span class="sxs-lookup"><span data-stu-id="199ea-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="199ea-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="199ea-126">Remarks</span></span>  
 <span data-ttu-id="199ea-127">O [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)e `EndConnection`, para associar listas de tarefas com identificadores e nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="199ea-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="199ea-128">Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="199ea-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="199ea-129">`BeginConnection` é chamado primeiro para estabelecer uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="199ea-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="199ea-130">`SetConnectionTasks` é chamado ao lado de fornecer o conjunto de tarefas a ser associado a essa conexão.</span><span class="sxs-lookup"><span data-stu-id="199ea-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="199ea-131">`EndConnection` é chamado por último para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="199ea-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="199ea-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="199ea-132">Requirements</span></span>  
 <span data-ttu-id="199ea-133">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="199ea-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="199ea-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="199ea-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="199ea-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="199ea-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="199ea-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="199ea-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199ea-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="199ea-137">See also</span></span>

- [<span data-ttu-id="199ea-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="199ea-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="199ea-139">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="199ea-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="199ea-140">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="199ea-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="199ea-141">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="199ea-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="199ea-142">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="199ea-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
