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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf21e1844ea99b231054f8350ddacb8bb707a94e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200098"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="c395e-102">Método ICLRDebugManager::EndConnection</span><span class="sxs-lookup"><span data-stu-id="c395e-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="c395e-103">Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="c395e-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c395e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c395e-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c395e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c395e-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="c395e-106">[in] O identificador específico do host para a conexão e a lista associada das tarefas comuns de runtime (CLR) de linguagem.</span><span class="sxs-lookup"><span data-stu-id="c395e-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c395e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c395e-107">Return Value</span></span>  
  
|<span data-ttu-id="c395e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c395e-108">HRESULT</span></span>|<span data-ttu-id="c395e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c395e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c395e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c395e-110">S_OK</span></span>|`EndConnection` <span data-ttu-id="c395e-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c395e-111">returned successfully.</span></span>|  
|<span data-ttu-id="c395e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c395e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c395e-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c395e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c395e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c395e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c395e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c395e-115">The call timed out.</span></span>|  
|<span data-ttu-id="c395e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c395e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c395e-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c395e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c395e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c395e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c395e-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="c395e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c395e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c395e-120">E_FAIL</span></span>|<span data-ttu-id="c395e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c395e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c395e-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c395e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c395e-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c395e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c395e-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c395e-124">E_INVALIDARG</span></span>|<span data-ttu-id="c395e-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nunca foi chamado usando `dwConnectionId`, ou `dwConnectionId` foi zero.</span><span class="sxs-lookup"><span data-stu-id="c395e-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c395e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="c395e-126">Remarks</span></span>  
 <span data-ttu-id="c395e-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), e `EndConnection`, para a associação de listas de tarefas com identificadores e nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="c395e-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c395e-128">Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="c395e-128">These three methods must be called in a specific order for each set of tasks.</span></span> `BeginConnection` <span data-ttu-id="c395e-129">é chamado primeiro para estabelecer uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="c395e-129">is called first to establish a new connection.</span></span> `SetConnectionTasks` <span data-ttu-id="c395e-130">é chamado em seguida para fornecer o conjunto de tarefas a ser associado essa conexão.</span><span class="sxs-lookup"><span data-stu-id="c395e-130">is called next to provide the set of tasks to be associated with that connection.</span></span> `EndConnection` <span data-ttu-id="c395e-131">é chamado pela última vez para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="c395e-131">is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c395e-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c395e-132">Requirements</span></span>  
 <span data-ttu-id="c395e-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c395e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c395e-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c395e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c395e-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c395e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c395e-136">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c395e-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c395e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c395e-137">See also</span></span>

- [<span data-ttu-id="c395e-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="c395e-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c395e-139">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="c395e-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="c395e-140">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="c395e-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="c395e-141">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="c395e-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="c395e-142">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="c395e-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
