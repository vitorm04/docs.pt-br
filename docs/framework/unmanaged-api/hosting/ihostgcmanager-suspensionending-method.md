---
title: Método IHostGCManager::SuspensionEnding
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: 4c05ee766bf40be2e9c39f01c7e1b16cb9fab50d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804846"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="cacbd-102">Método IHostGCManager::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="cacbd-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="cacbd-103">Notifica o host que o Common Language Runtime (CLR) está retomando a execução de tarefas em threads que foram suspensos para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cacbd-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacbd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cacbd-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cacbd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cacbd-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="cacbd-106">no A geração de coleta de lixo que está acabando de ser concluída, da qual o thread está retomando.</span><span class="sxs-lookup"><span data-stu-id="cacbd-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cacbd-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="cacbd-107">Return Value</span></span>  
  
|<span data-ttu-id="cacbd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cacbd-108">HRESULT</span></span>|<span data-ttu-id="cacbd-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cacbd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cacbd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cacbd-110">S_OK</span></span>|<span data-ttu-id="cacbd-111">`SuspensionEnding`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="cacbd-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="cacbd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cacbd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cacbd-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="cacbd-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cacbd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cacbd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cacbd-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="cacbd-115">The call timed out.</span></span>|  
|<span data-ttu-id="cacbd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cacbd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cacbd-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="cacbd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cacbd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cacbd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cacbd-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="cacbd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cacbd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cacbd-120">E_FAIL</span></span>|<span data-ttu-id="cacbd-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="cacbd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cacbd-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="cacbd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cacbd-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cacbd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cacbd-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="cacbd-124">Remarks</span></span>  
 <span data-ttu-id="cacbd-125">O CLR chama `SuspensionEnding` após executar uma coleta de lixo para informar ao host que o thread está retomando a execução.</span><span class="sxs-lookup"><span data-stu-id="cacbd-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cacbd-126">Não reagende o thread a partir do qual a chamada de método foi feita.</span><span class="sxs-lookup"><span data-stu-id="cacbd-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cacbd-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cacbd-127">Requirements</span></span>  
 <span data-ttu-id="cacbd-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cacbd-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cacbd-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cacbd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cacbd-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cacbd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cacbd-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cacbd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cacbd-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="cacbd-132">See also</span></span>

- [<span data-ttu-id="cacbd-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="cacbd-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="cacbd-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="cacbd-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="cacbd-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="cacbd-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="cacbd-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="cacbd-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="cacbd-137">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="cacbd-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
