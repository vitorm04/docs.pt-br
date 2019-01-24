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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf915af48262a0f48e85623de95b76ad94d860b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573290"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="57863-102">Método IHostGCManager::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="57863-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="57863-103">Notifica o host que o common language runtime (CLR) está continuando a execução de tarefas em threads que tinham sido suspensos para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="57863-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57863-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57863-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57863-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57863-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="57863-106">[in] A geração de coleta de lixo está finalizando, do qual o thread está continuando.</span><span class="sxs-lookup"><span data-stu-id="57863-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57863-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="57863-107">Return Value</span></span>  
  
|<span data-ttu-id="57863-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57863-108">HRESULT</span></span>|<span data-ttu-id="57863-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="57863-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57863-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57863-110">S_OK</span></span>|<span data-ttu-id="57863-111">`SuspensionEnding` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="57863-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="57863-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57863-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57863-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="57863-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57863-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57863-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57863-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="57863-115">The call timed out.</span></span>|  
|<span data-ttu-id="57863-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57863-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57863-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="57863-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57863-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57863-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57863-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="57863-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57863-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57863-120">E_FAIL</span></span>|<span data-ttu-id="57863-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="57863-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57863-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="57863-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57863-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57863-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57863-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="57863-124">Remarks</span></span>  
 <span data-ttu-id="57863-125">O CLR chama `SuspensionEnding` depois que ele executa uma coleta de lixo, para informar o host que o thread está continuando a execução.</span><span class="sxs-lookup"><span data-stu-id="57863-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="57863-126">Não reagende o thread de de que chamada de método foi feita.</span><span class="sxs-lookup"><span data-stu-id="57863-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57863-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57863-127">Requirements</span></span>  
 <span data-ttu-id="57863-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57863-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57863-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57863-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57863-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="57863-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57863-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57863-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57863-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57863-132">See also</span></span>
- [<span data-ttu-id="57863-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="57863-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="57863-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="57863-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="57863-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="57863-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="57863-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="57863-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="57863-137">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="57863-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
