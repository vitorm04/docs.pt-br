---
title: Método ICLRTask::SetTaskIdentifier
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: cf6d84e483188ea7ed3376ba9b28906a38913fd4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124631"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="71e8f-102">Método ICLRTask::SetTaskIdentifier</span><span class="sxs-lookup"><span data-stu-id="71e8f-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="71e8f-103">Instrui o Common Language Runtime (CLR) a associar o valor do identificador especificado à tarefa representada pela instância de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="71e8f-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e8f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71e8f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71e8f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71e8f-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="71e8f-106">no O identificador exclusivo do Common Language Runtime a ser associado à tarefa representada pela instância de `ICLRTask` atual.</span><span class="sxs-lookup"><span data-stu-id="71e8f-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71e8f-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="71e8f-107">Return Value</span></span>  
  
|<span data-ttu-id="71e8f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71e8f-108">HRESULT</span></span>|<span data-ttu-id="71e8f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="71e8f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71e8f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="71e8f-110">S_OK</span></span>|<span data-ttu-id="71e8f-111">`SetTaskIdentifier` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="71e8f-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="71e8f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71e8f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71e8f-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="71e8f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71e8f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71e8f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71e8f-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="71e8f-115">The call timed out.</span></span>|  
|<span data-ttu-id="71e8f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71e8f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71e8f-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="71e8f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71e8f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71e8f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71e8f-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="71e8f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71e8f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71e8f-120">E_FAIL</span></span>|<span data-ttu-id="71e8f-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="71e8f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71e8f-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="71e8f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71e8f-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="71e8f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71e8f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="71e8f-124">Remarks</span></span>  
 <span data-ttu-id="71e8f-125">O host pode associar um identificador a uma tarefa para ajudar a integrar o CLR e o host em um ambiente de depuração.</span><span class="sxs-lookup"><span data-stu-id="71e8f-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="71e8f-126">O identificador não tem significado para o CLR.</span><span class="sxs-lookup"><span data-stu-id="71e8f-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="71e8f-127">O CLR passa isso para um aplicativo de depurador.</span><span class="sxs-lookup"><span data-stu-id="71e8f-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="71e8f-128">O depurador pode usar esse identificador para associar uma pilha de chamadas CLR a uma pilha de chamadas do host e habilitar suas respectivas informações de rastreamento para serem unificadas quando exibidas na interface do usuário do depurador.</span><span class="sxs-lookup"><span data-stu-id="71e8f-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71e8f-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71e8f-129">Requirements</span></span>  
 <span data-ttu-id="71e8f-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71e8f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71e8f-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="71e8f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71e8f-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="71e8f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71e8f-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71e8f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e8f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71e8f-134">See also</span></span>

- [<span data-ttu-id="71e8f-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="71e8f-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="71e8f-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="71e8f-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="71e8f-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="71e8f-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="71e8f-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="71e8f-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
