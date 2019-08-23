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
ms.openlocfilehash: fb78026f875c18a557951108518c9280f5eb567d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937676"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="c57d8-102">Método IHostGCManager::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="c57d8-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="c57d8-103">Notifica o host de que o thread do qual a chamada de método foi feita está prestes a ser bloqueado para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c57d8-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c57d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c57d8-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c57d8-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c57d8-105">Return Value</span></span>  
  
|<span data-ttu-id="c57d8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c57d8-106">HRESULT</span></span>|<span data-ttu-id="c57d8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c57d8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c57d8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c57d8-108">S_OK</span></span>|<span data-ttu-id="c57d8-109">`ThreadIsBlockingForSuspension`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c57d8-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="c57d8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c57d8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c57d8-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c57d8-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c57d8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c57d8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c57d8-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c57d8-113">The call timed out.</span></span>|  
|<span data-ttu-id="c57d8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c57d8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c57d8-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c57d8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c57d8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c57d8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c57d8-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="c57d8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c57d8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c57d8-118">E_FAIL</span></span>|<span data-ttu-id="c57d8-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c57d8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c57d8-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="c57d8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c57d8-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c57d8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c57d8-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c57d8-122">Remarks</span></span>  
 <span data-ttu-id="c57d8-123">O CLR normalmente chama o `ThreadIsBlockForSuspension` método em preparação para uma coleta de lixo, para dar ao host uma oportunidade de reagendar o thread para tarefas não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="c57d8-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c57d8-124">O host pode reagendar tarefas somente após uma chamada `ThreadIsBlockingForSuspension`para.</span><span class="sxs-lookup"><span data-stu-id="c57d8-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="c57d8-125">Depois que o tempo de execução chama [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), o host não deve reagendar uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="c57d8-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c57d8-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c57d8-126">Requirements</span></span>  
 <span data-ttu-id="c57d8-127">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c57d8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c57d8-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c57d8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c57d8-129">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c57d8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c57d8-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c57d8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57d8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c57d8-131">See also</span></span>

- [<span data-ttu-id="c57d8-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="c57d8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c57d8-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="c57d8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c57d8-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="c57d8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c57d8-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="c57d8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="c57d8-136">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="c57d8-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
