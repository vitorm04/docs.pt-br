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
ms.openlocfilehash: e1b93356fd40aacdec2e764946e3e3b12d0bd306
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762936"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="a6a2d-102">Método ICLRTask::SetTaskIdentifier</span><span class="sxs-lookup"><span data-stu-id="a6a2d-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="a6a2d-103">Instrui o Common Language Runtime (CLR) a associar o valor do identificador especificado à tarefa representada pela instância de [ICLRTask](iclrtask-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a2d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6a2d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6a2d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6a2d-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="a6a2d-106">no O identificador exclusivo do Common Language Runtime a ser associado à tarefa representada pela `ICLRTask` instância atual.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6a2d-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="a6a2d-107">Return Value</span></span>  
  
|<span data-ttu-id="a6a2d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6a2d-108">HRESULT</span></span>|<span data-ttu-id="a6a2d-109">Description</span><span class="sxs-lookup"><span data-stu-id="a6a2d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6a2d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6a2d-110">S_OK</span></span>|<span data-ttu-id="a6a2d-111">`SetTaskIdentifier`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="a6a2d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6a2d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6a2d-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6a2d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6a2d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6a2d-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-115">The call timed out.</span></span>|  
|<span data-ttu-id="a6a2d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6a2d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6a2d-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6a2d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6a2d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6a2d-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6a2d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6a2d-120">E_FAIL</span></span>|<span data-ttu-id="a6a2d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6a2d-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6a2d-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6a2d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6a2d-124">Remarks</span></span>  
 <span data-ttu-id="a6a2d-125">O host pode associar um identificador a uma tarefa para ajudar a integrar o CLR e o host em um ambiente de depuração.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="a6a2d-126">O identificador não tem significado para o CLR.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="a6a2d-127">O CLR passa isso para um aplicativo de depurador.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="a6a2d-128">O depurador pode usar esse identificador para associar uma pilha de chamadas CLR a uma pilha de chamadas do host e habilitar suas respectivas informações de rastreamento para serem unificadas quando exibidas na interface do usuário do depurador.</span><span class="sxs-lookup"><span data-stu-id="a6a2d-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6a2d-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6a2d-129">Requirements</span></span>  
 <span data-ttu-id="a6a2d-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6a2d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a2d-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a6a2d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6a2d-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a6a2d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6a2d-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a2d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a2d-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="a6a2d-134">See also</span></span>

- [<span data-ttu-id="a6a2d-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="a6a2d-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a6a2d-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="a6a2d-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a6a2d-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="a6a2d-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a6a2d-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="a6a2d-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
