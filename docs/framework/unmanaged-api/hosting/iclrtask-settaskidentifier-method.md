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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fe678dbf47141c31fb0870f1364983bc2ad69fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770414"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="dbe34-102">Método ICLRTask::SetTaskIdentifier</span><span class="sxs-lookup"><span data-stu-id="dbe34-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="dbe34-103">Instrui o common language runtime (CLR) para associar o valor do identificador especificado à tarefa representada por atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="dbe34-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe34-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbe34-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbe34-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbe34-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="dbe34-106">[in] O identificador exclusivo para o common language runtime associar à tarefa representada por atual `ICLRTask` instância.</span><span class="sxs-lookup"><span data-stu-id="dbe34-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbe34-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dbe34-107">Return Value</span></span>  
  
|<span data-ttu-id="dbe34-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbe34-108">HRESULT</span></span>|<span data-ttu-id="dbe34-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbe34-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbe34-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbe34-110">S_OK</span></span>|<span data-ttu-id="dbe34-111">`SetTaskIdentifier` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dbe34-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="dbe34-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbe34-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbe34-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="dbe34-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbe34-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbe34-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbe34-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="dbe34-115">The call timed out.</span></span>|  
|<span data-ttu-id="dbe34-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbe34-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbe34-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="dbe34-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbe34-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbe34-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbe34-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="dbe34-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbe34-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbe34-120">E_FAIL</span></span>|<span data-ttu-id="dbe34-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dbe34-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbe34-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="dbe34-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbe34-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbe34-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe34-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbe34-124">Remarks</span></span>  
 <span data-ttu-id="dbe34-125">O host pode associar um identificador de uma tarefa para ajudar na integração CLR e o host em um ambiente de depuração.</span><span class="sxs-lookup"><span data-stu-id="dbe34-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="dbe34-126">O identificador não tem nenhum significado para o CLR.</span><span class="sxs-lookup"><span data-stu-id="dbe34-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="dbe34-127">O CLR passa para um aplicativo do depurador.</span><span class="sxs-lookup"><span data-stu-id="dbe34-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="dbe34-128">O depurador pode usar esse identificador para associar a uma pilha de chamadas do host de uma pilha de chamadas CLR e ativar suas informações de rastreamento respectivos ser unificados quando exibido na interface do usuário do depurador.</span><span class="sxs-lookup"><span data-stu-id="dbe34-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe34-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbe34-129">Requirements</span></span>  
 <span data-ttu-id="dbe34-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbe34-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe34-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbe34-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbe34-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dbe34-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbe34-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe34-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe34-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbe34-134">See also</span></span>

- [<span data-ttu-id="dbe34-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="dbe34-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="dbe34-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="dbe34-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dbe34-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="dbe34-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dbe34-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="dbe34-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
