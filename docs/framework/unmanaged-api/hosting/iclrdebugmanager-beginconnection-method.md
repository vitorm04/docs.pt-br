---
title: Método ICLRDebugManager::BeginConnection
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b365aaa13b3070662a74ebcfc914f5ed3d291d76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133985"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="658f6-102">Método ICLRDebugManager::BeginConnection</span><span class="sxs-lookup"><span data-stu-id="658f6-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="658f6-103">Estabelece uma nova conexão entre o host e o depurador para associar uma lista de tarefas com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="658f6-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="658f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="658f6-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="658f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="658f6-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="658f6-106">[in] Um identificador para associar a lista de tarefas comuns de language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="658f6-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="658f6-107">[in] Um nome amigável para associar a lista de tarefas CLR.</span><span class="sxs-lookup"><span data-stu-id="658f6-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="658f6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="658f6-108">Return Value</span></span>  
  
|<span data-ttu-id="658f6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="658f6-109">HRESULT</span></span>|<span data-ttu-id="658f6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="658f6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="658f6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="658f6-111">S_OK</span></span>|<span data-ttu-id="658f6-112">`BeginConnection` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="658f6-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="658f6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="658f6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="658f6-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="658f6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="658f6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="658f6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="658f6-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="658f6-116">The call timed out.</span></span>|  
|<span data-ttu-id="658f6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="658f6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="658f6-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="658f6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="658f6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="658f6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="658f6-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="658f6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="658f6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="658f6-121">E_FAIL</span></span>|<span data-ttu-id="658f6-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="658f6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="658f6-123">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="658f6-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="658f6-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="658f6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="658f6-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="658f6-125">E_INVALIDARG</span></span>|<span data-ttu-id="658f6-126">`dwConnectionId` era zero, ou `BeginConnection` já foi chamado usando este `dwConnectionId` valor, ou `szConnectionName` era nulo.</span><span class="sxs-lookup"><span data-stu-id="658f6-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="658f6-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="658f6-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="658f6-128">Não há memória suficiente pode ser alocada para armazenar a lista de tarefas associadas a essa conexão.</span><span class="sxs-lookup"><span data-stu-id="658f6-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="658f6-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="658f6-129">Remarks</span></span>  
 <span data-ttu-id="658f6-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), e [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), para a associação de listas de tarefas com identificadores e nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="658f6-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="658f6-131">Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="658f6-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="658f6-132">`BeginConnection` é chamado primeiro para estabelecer uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="658f6-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="658f6-133">`SetConnectionTasks` é chamado em seguida para fornecer o conjunto de tarefas a ser associado essa conexão.</span><span class="sxs-lookup"><span data-stu-id="658f6-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="658f6-134">`EndConnection` é chamado pela última vez para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="658f6-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="658f6-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="658f6-135">Requirements</span></span>  
 <span data-ttu-id="658f6-136">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="658f6-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="658f6-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="658f6-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="658f6-138">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="658f6-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="658f6-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="658f6-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658f6-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="658f6-140">See also</span></span>

- [<span data-ttu-id="658f6-141">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="658f6-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="658f6-142">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="658f6-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="658f6-143">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="658f6-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="658f6-144">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="658f6-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="658f6-145">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="658f6-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
