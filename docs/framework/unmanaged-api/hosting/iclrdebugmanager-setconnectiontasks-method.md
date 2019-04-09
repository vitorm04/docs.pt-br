---
title: Método ICLRDebugManager::SetConnectionTasks
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88078fa34910dca642eae3cf261c9e00fae4f27a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201982"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="9e785-102">Método ICLRDebugManager::SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="9e785-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="9e785-103">Associa uma lista dos [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instâncias com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="9e785-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e785-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e785-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e785-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e785-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="9e785-106">[in] O identificador específico do host para a conexão ao qual associar o `ppCLRTask` matriz.</span><span class="sxs-lookup"><span data-stu-id="9e785-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="9e785-107">[in] O número de membros de `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="9e785-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="9e785-108">Esse número deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="9e785-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="9e785-109">[in] Uma matriz de `ICLRTask` ponteiros para associar com a conexão identificado pelo `id`.</span><span class="sxs-lookup"><span data-stu-id="9e785-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="9e785-110">Essa matriz deve conter pelo menos um membro.</span><span class="sxs-lookup"><span data-stu-id="9e785-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e785-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9e785-111">Return Value</span></span>  
  
|<span data-ttu-id="9e785-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e785-112">HRESULT</span></span>|<span data-ttu-id="9e785-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e785-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e785-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e785-114">S_OK</span></span>|`SetConnectionTasks` <span data-ttu-id="9e785-115">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9e785-115">returned successfully.</span></span>|  
|<span data-ttu-id="9e785-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e785-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e785-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9e785-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e785-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e785-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e785-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9e785-119">The call timed out.</span></span>|  
|<span data-ttu-id="9e785-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e785-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e785-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9e785-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e785-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e785-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e785-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="9e785-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e785-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e785-124">E_FAIL</span></span>|<span data-ttu-id="9e785-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9e785-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e785-126">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="9e785-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e785-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e785-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9e785-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9e785-128">E_INVALIDARG</span></span>|<span data-ttu-id="9e785-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) não foi chamado usando esse valor de `id`, ou `dwCount` ou `id` é zero, ou um dos elementos da `ppCLRTask` é nulo.</span><span class="sxs-lookup"><span data-stu-id="9e785-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e785-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e785-130">Remarks</span></span>  
 <span data-ttu-id="9e785-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos, `BeginConnection`, `SetConnectionTasks`, e [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), para a associação de listas de tarefas com identificadores e nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="9e785-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e785-132">Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="9e785-132">These three methods must be called in a specific order for each set of tasks.</span></span> `BeginConnection` <span data-ttu-id="9e785-133">é chamado primeiro para estabelecer uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="9e785-133">is called first to establish a new connection.</span></span> `SetConnectionTasks` <span data-ttu-id="9e785-134">é chamado em seguida para fornecer o conjunto de tarefas a ser associado essa conexão.</span><span class="sxs-lookup"><span data-stu-id="9e785-134">is called next to provide the set of tasks to be associated with that connection.</span></span> `EndConnection` <span data-ttu-id="9e785-135">é chamado pela última vez para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="9e785-135">is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e785-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e785-136">Requirements</span></span>  
 <span data-ttu-id="9e785-137">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e785-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e785-138">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e785-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e785-139">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9e785-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9e785-140">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9e785-140">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e785-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e785-141">See also</span></span>

- [<span data-ttu-id="9e785-142">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9e785-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9e785-143">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="9e785-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="9e785-144">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="9e785-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="9e785-145">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="9e785-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="9e785-146">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="9e785-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
