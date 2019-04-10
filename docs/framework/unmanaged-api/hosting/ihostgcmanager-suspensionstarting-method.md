---
title: Método IHostGCManager::SuspensionStarting
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ef5bb2539820d5a7bcd4ca6b4de86564290709
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213084"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="ffa6d-102">Método IHostGCManager::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="ffa6d-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="ffa6d-103">Notifica o host que o common language runtime (CLR) está suspendendo a execução de tarefas para executar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa6d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffa6d-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ffa6d-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ffa6d-105">Return Value</span></span>  
  
|<span data-ttu-id="ffa6d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffa6d-106">HRESULT</span></span>|<span data-ttu-id="ffa6d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffa6d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffa6d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffa6d-108">S_OK</span></span>|`SuspensionStarting` <span data-ttu-id="ffa6d-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-109">returned successfully.</span></span>|  
|<span data-ttu-id="ffa6d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffa6d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffa6d-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffa6d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffa6d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffa6d-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-113">The call timed out.</span></span>|  
|<span data-ttu-id="ffa6d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffa6d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffa6d-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffa6d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffa6d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffa6d-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffa6d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffa6d-118">E_FAIL</span></span>|<span data-ttu-id="ffa6d-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffa6d-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffa6d-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffa6d-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffa6d-122">Remarks</span></span>  
 <span data-ttu-id="ffa6d-123">O CLR chama `SuspensionStarting` para informar o host que a coleta de lixo está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffa6d-124">Não reagende essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-124">Do not reschedule this task.</span></span> <span data-ttu-id="ffa6d-125">O host deve reagendar uma tarefa quando [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="ffa6d-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffa6d-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffa6d-126">Requirements</span></span>  
 <span data-ttu-id="ffa6d-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa6d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa6d-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffa6d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffa6d-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ffa6d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ffa6d-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ffa6d-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ffa6d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffa6d-131">See also</span></span>

- [<span data-ttu-id="ffa6d-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="ffa6d-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ffa6d-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="ffa6d-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ffa6d-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="ffa6d-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ffa6d-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="ffa6d-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="ffa6d-136">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="ffa6d-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
