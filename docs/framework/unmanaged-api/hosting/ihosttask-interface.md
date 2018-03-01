---
title: Interface IHostTask
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bbffe2a171c112d4e9650b2c1b2a9ce1f010f382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttask-interface"></a><span data-ttu-id="01e91-102">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="01e91-102">IHostTask Interface</span></span>
<span data-ttu-id="01e91-103">Fornece métodos que permitem que o common language runtime (CLR) para se comunicar com o host para gerenciar as tarefas.</span><span class="sxs-lookup"><span data-stu-id="01e91-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01e91-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="01e91-104">Methods</span></span>  
  
|<span data-ttu-id="01e91-105">Método</span><span class="sxs-lookup"><span data-stu-id="01e91-105">Method</span></span>|<span data-ttu-id="01e91-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="01e91-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01e91-107">Método Alert</span><span class="sxs-lookup"><span data-stu-id="01e91-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="01e91-108">Solicitações que o host de ativação da tarefa representada pela atual `IHostTask` instância, para que a tarefa pode ser anulada.</span><span class="sxs-lookup"><span data-stu-id="01e91-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="01e91-109">Método GetPriority</span><span class="sxs-lookup"><span data-stu-id="01e91-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="01e91-110">Obtém o nível de prioridade de thread da tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="01e91-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="01e91-111">Método Join</span><span class="sxs-lookup"><span data-stu-id="01e91-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="01e91-112">Bloqueia a tarefa chamada até que a tarefa representada por atual `IHostTask` instância for concluída, o intervalo de tempo especificado expira, ou [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="01e91-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="01e91-113">Método SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="01e91-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="01e91-114">Associa um [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância com a atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="01e91-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="01e91-115">Método SetPriority</span><span class="sxs-lookup"><span data-stu-id="01e91-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="01e91-116">Nível de solicitações que o host de ajustar a prioridade de thread para a tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="01e91-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="01e91-117">Método Start</span><span class="sxs-lookup"><span data-stu-id="01e91-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="01e91-118">O host de move a tarefa representada por atual de solicitações `IHostTask` instância de um estado suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="01e91-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01e91-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="01e91-119">Remarks</span></span>  
 <span data-ttu-id="01e91-120">O CLR chama métodos definidos pelo `IHostTask` para iniciar uma tarefa, defina a prioridade de thread nível, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="01e91-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e91-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01e91-121">Requirements</span></span>  
 <span data-ttu-id="01e91-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01e91-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e91-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01e91-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01e91-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="01e91-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01e91-125">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e91-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e91-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01e91-126">See Also</span></span>  
 [<span data-ttu-id="01e91-127">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="01e91-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="01e91-128">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="01e91-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="01e91-129">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="01e91-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="01e91-130">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="01e91-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
