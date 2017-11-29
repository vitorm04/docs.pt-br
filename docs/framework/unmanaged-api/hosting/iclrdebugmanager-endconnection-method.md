---
title: "Método ICLRDebugManager::EndConnection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.EndConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 114f2217d22fc270b03d271db4acc44f0edbcca8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="426cf-102">Método ICLRDebugManager::EndConnection</span><span class="sxs-lookup"><span data-stu-id="426cf-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="426cf-103">Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="426cf-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="426cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="426cf-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="426cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="426cf-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="426cf-106">[in] O identificador de host específico para a conexão e a lista de associados de tarefas comuns de tempo de execução (CLR) do idioma.</span><span class="sxs-lookup"><span data-stu-id="426cf-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="426cf-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="426cf-107">Return Value</span></span>  
  
|<span data-ttu-id="426cf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="426cf-108">HRESULT</span></span>|<span data-ttu-id="426cf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="426cf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="426cf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="426cf-110">S_OK</span></span>|<span data-ttu-id="426cf-111">`EndConnection`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="426cf-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="426cf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="426cf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="426cf-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="426cf-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="426cf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="426cf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="426cf-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="426cf-115">The call timed out.</span></span>|  
|<span data-ttu-id="426cf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="426cf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="426cf-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="426cf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="426cf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="426cf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="426cf-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="426cf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="426cf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="426cf-120">E_FAIL</span></span>|<span data-ttu-id="426cf-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="426cf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="426cf-122">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="426cf-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="426cf-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="426cf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="426cf-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="426cf-124">E_INVALIDARG</span></span>|<span data-ttu-id="426cf-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nunca foi chamado usando `dwConnectionId`, ou `dwConnectionId` era zero.</span><span class="sxs-lookup"><span data-stu-id="426cf-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="426cf-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="426cf-126">Remarks</span></span>  
 <span data-ttu-id="426cf-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), e `EndConnection`, para a associação de listas de tarefas com identificadores e nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="426cf-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="426cf-128">Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="426cf-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="426cf-129">`BeginConnection`é chamado primeiro para estabelecer uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="426cf-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="426cf-130">`SetConnectionTasks`é chamado de lado para fornecer o conjunto de tarefas a ser associado essa conexão.</span><span class="sxs-lookup"><span data-stu-id="426cf-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="426cf-131">`EndConnection`é chamado de última para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="426cf-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="426cf-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="426cf-132">Requirements</span></span>  
 <span data-ttu-id="426cf-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="426cf-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="426cf-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="426cf-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="426cf-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="426cf-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="426cf-136">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="426cf-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="426cf-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="426cf-137">See Also</span></span>  
 [<span data-ttu-id="426cf-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="426cf-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="426cf-139">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="426cf-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="426cf-140">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="426cf-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="426cf-141">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="426cf-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="426cf-142">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="426cf-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
