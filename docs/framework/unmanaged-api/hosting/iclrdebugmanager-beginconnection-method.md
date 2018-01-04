---
title: "Método ICLRDebugManager::BeginConnection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.BeginConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a637ba71dc966cf311526f468393ef4207e10460
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="96fdf-102">Método ICLRDebugManager::BeginConnection</span><span class="sxs-lookup"><span data-stu-id="96fdf-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="96fdf-103">Estabelece uma nova conexão entre o host e o depurador para associar uma lista de tarefas com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="96fdf-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96fdf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96fdf-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96fdf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96fdf-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="96fdf-106">[in] Um identificador para associar a lista de tarefas comuns de tempo de execução (CLR) do idioma.</span><span class="sxs-lookup"><span data-stu-id="96fdf-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="96fdf-107">[in] Um nome amigável para associar a lista de tarefas CLR.</span><span class="sxs-lookup"><span data-stu-id="96fdf-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96fdf-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="96fdf-108">Return Value</span></span>  
  
|<span data-ttu-id="96fdf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96fdf-109">HRESULT</span></span>|<span data-ttu-id="96fdf-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="96fdf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96fdf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="96fdf-111">S_OK</span></span>|<span data-ttu-id="96fdf-112">`BeginConnection`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="96fdf-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="96fdf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="96fdf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="96fdf-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="96fdf-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="96fdf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="96fdf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="96fdf-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="96fdf-116">The call timed out.</span></span>|  
|<span data-ttu-id="96fdf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="96fdf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="96fdf-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="96fdf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="96fdf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="96fdf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="96fdf-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="96fdf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="96fdf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="96fdf-121">E_FAIL</span></span>|<span data-ttu-id="96fdf-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="96fdf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="96fdf-123">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="96fdf-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="96fdf-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="96fdf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="96fdf-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="96fdf-125">E_INVALIDARG</span></span>|<span data-ttu-id="96fdf-126">`dwConnectionId`era zero, ou `BeginConnection` já foi chamado usando esse `dwConnectionId` valor, ou `szConnectionName` era nulo.</span><span class="sxs-lookup"><span data-stu-id="96fdf-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="96fdf-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="96fdf-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="96fdf-128">Memória insuficiente pode ser alocada para armazenar a lista de tarefas associadas a esta conexão.</span><span class="sxs-lookup"><span data-stu-id="96fdf-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96fdf-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="96fdf-129">Remarks</span></span>  
 <span data-ttu-id="96fdf-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), e [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), para a associação de listas de tarefas com identificadores e nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="96fdf-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96fdf-131">Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="96fdf-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="96fdf-132">`BeginConnection`é chamado primeiro para estabelecer uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="96fdf-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="96fdf-133">`SetConnectionTasks`é chamado de lado para fornecer o conjunto de tarefas a ser associado essa conexão.</span><span class="sxs-lookup"><span data-stu-id="96fdf-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="96fdf-134">`EndConnection`é chamado de última para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="96fdf-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96fdf-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96fdf-135">Requirements</span></span>  
 <span data-ttu-id="96fdf-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96fdf-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96fdf-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96fdf-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96fdf-138">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="96fdf-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96fdf-139">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96fdf-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96fdf-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96fdf-140">See Also</span></span>  
 [<span data-ttu-id="96fdf-141">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="96fdf-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="96fdf-142">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="96fdf-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="96fdf-143">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="96fdf-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="96fdf-144">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="96fdf-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="96fdf-145">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="96fdf-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
