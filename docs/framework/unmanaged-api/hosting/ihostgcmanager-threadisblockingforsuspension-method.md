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
ms.openlocfilehash: 85921156860f52eb2a898e6be356e191c2a4f02d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439264"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="54882-102">Método IHostGCManager::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="54882-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="54882-103">Notifica o host que o thread do qual foi feita a chamada do método está prestes a bloquear uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="54882-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54882-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54882-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="54882-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="54882-105">Return Value</span></span>  
  
|<span data-ttu-id="54882-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54882-106">HRESULT</span></span>|<span data-ttu-id="54882-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="54882-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54882-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="54882-108">S_OK</span></span>|<span data-ttu-id="54882-109">`ThreadIsBlockingForSuspension` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="54882-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="54882-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54882-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54882-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="54882-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54882-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54882-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54882-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="54882-113">The call timed out.</span></span>|  
|<span data-ttu-id="54882-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54882-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54882-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="54882-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54882-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54882-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54882-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="54882-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54882-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54882-118">E_FAIL</span></span>|<span data-ttu-id="54882-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="54882-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54882-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="54882-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54882-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="54882-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54882-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="54882-122">Remarks</span></span>  
 <span data-ttu-id="54882-123">O CLR chama normalmente o `ThreadIsBlockForSuspension` método em preparação para uma coleta de lixo, para que o host tenha a oportunidade para reagendar o thread para tarefas não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="54882-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54882-124">O host pode reagendar tarefas apenas após uma chamada para `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="54882-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="54882-125">Depois de chamar o tempo de execução [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), o host não deve reagendar uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="54882-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54882-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54882-126">Requirements</span></span>  
 <span data-ttu-id="54882-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54882-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54882-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54882-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54882-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="54882-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54882-130">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54882-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54882-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54882-131">See Also</span></span>  
 [<span data-ttu-id="54882-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="54882-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="54882-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="54882-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="54882-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="54882-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="54882-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="54882-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="54882-136">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="54882-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
