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
ms.openlocfilehash: 9f2835c9846657edffc745c435211f93b20f7173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438828"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="1d1a0-102">Método IHostGCManager::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="1d1a0-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="1d1a0-103">Notifica o host que o common language runtime (CLR) está continuando a execução de tarefas em threads que foi suspenso para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d1a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d1a0-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d1a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d1a0-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="1d1a0-106">[in] A geração de coleta de lixo está finalizando, do qual o thread está continuando.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d1a0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1d1a0-107">Return Value</span></span>  
  
|<span data-ttu-id="1d1a0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d1a0-108">HRESULT</span></span>|<span data-ttu-id="1d1a0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d1a0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d1a0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d1a0-110">S_OK</span></span>|<span data-ttu-id="1d1a0-111">`SuspensionEnding` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="1d1a0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d1a0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d1a0-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d1a0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d1a0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d1a0-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-115">The call timed out.</span></span>|  
|<span data-ttu-id="1d1a0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d1a0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d1a0-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d1a0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d1a0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d1a0-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d1a0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d1a0-120">E_FAIL</span></span>|<span data-ttu-id="1d1a0-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d1a0-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d1a0-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d1a0-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d1a0-124">Remarks</span></span>  
 <span data-ttu-id="1d1a0-125">O CLR chama `SuspensionEnding` depois que ele executa uma coleta de lixo, para informar o host que o thread está continuando a execução.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d1a0-126">Não reagende o thread de de que chamada de método foi feita.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d1a0-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d1a0-127">Requirements</span></span>  
 <span data-ttu-id="1d1a0-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d1a0-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d1a0-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d1a0-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d1a0-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1d1a0-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d1a0-131">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d1a0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1a0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d1a0-132">See Also</span></span>  
 [<span data-ttu-id="1d1a0-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="1d1a0-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1d1a0-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="1d1a0-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1d1a0-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="1d1a0-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1d1a0-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="1d1a0-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="1d1a0-137">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="1d1a0-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
