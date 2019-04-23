---
title: Método IHostGCManager::ThreadIsBlockingForSuspension
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 740f408b84dad67ee20c2508ae42a9569ed095f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179862"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="0ad69-102">Método IHostGCManager::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="0ad69-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="0ad69-103">Notifica o host que o thread do qual a chamada de método foi feita está prestes a bloquear uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0ad69-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ad69-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0ad69-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0ad69-105">Return Value</span></span>  
  
|<span data-ttu-id="0ad69-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ad69-106">HRESULT</span></span>|<span data-ttu-id="0ad69-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ad69-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ad69-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ad69-108">S_OK</span></span>|<span data-ttu-id="0ad69-109">`ThreadIsBlockingForSuspension` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ad69-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="0ad69-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ad69-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ad69-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ad69-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ad69-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ad69-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ad69-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0ad69-113">The call timed out.</span></span>|  
|<span data-ttu-id="0ad69-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ad69-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ad69-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0ad69-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ad69-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ad69-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ad69-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="0ad69-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ad69-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ad69-118">E_FAIL</span></span>|<span data-ttu-id="0ad69-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0ad69-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ad69-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0ad69-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ad69-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ad69-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ad69-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ad69-122">Remarks</span></span>  
 <span data-ttu-id="0ad69-123">O CLR chama normalmente o `ThreadIsBlockForSuspension` método em preparação para uma coleta de lixo, para que o host a oportunidade para reagendar o thread para tarefas não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="0ad69-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0ad69-124">O host pode reagendar tarefas somente após uma chamada para `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="0ad69-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="0ad69-125">Após a tempo de execução chama [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), o host não deve reagendar uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="0ad69-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ad69-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ad69-126">Requirements</span></span>  
 <span data-ttu-id="0ad69-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ad69-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ad69-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ad69-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ad69-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0ad69-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ad69-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ad69-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad69-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ad69-131">See also</span></span>

- [<span data-ttu-id="0ad69-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="0ad69-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0ad69-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="0ad69-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0ad69-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="0ad69-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0ad69-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="0ad69-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="0ad69-136">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="0ad69-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
