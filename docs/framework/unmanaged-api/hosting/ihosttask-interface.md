---
title: Interface IHostTask
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081496"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="939d7-102">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="939d7-102">IHostTask Interface</span></span>
<span data-ttu-id="939d7-103">Fornece métodos que permitem que o common language runtime (CLR) para se comunicar com o host para gerenciar tarefas.</span><span class="sxs-lookup"><span data-stu-id="939d7-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="939d7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="939d7-104">Methods</span></span>  
  
|<span data-ttu-id="939d7-105">Método</span><span class="sxs-lookup"><span data-stu-id="939d7-105">Method</span></span>|<span data-ttu-id="939d7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="939d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="939d7-107">Método Alert</span><span class="sxs-lookup"><span data-stu-id="939d7-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="939d7-108">Solicitações que o host ativar a tarefa representada por atual `IHostTask` da instância, portanto, a tarefa pode ser anulada.</span><span class="sxs-lookup"><span data-stu-id="939d7-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="939d7-109">Método GetPriority</span><span class="sxs-lookup"><span data-stu-id="939d7-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="939d7-110">Obtém o nível de prioridade do thread da tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="939d7-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="939d7-111">Método Join</span><span class="sxs-lookup"><span data-stu-id="939d7-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="939d7-112">Bloqueia a tarefa de chamada até que a tarefa representada por atual `IHostTask` instância é concluída, o intervalo de tempo especificado tenha decorrido, ou [ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="939d7-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="939d7-113">Método SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="939d7-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="939d7-114">Associa um [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância com o atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="939d7-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="939d7-115">Método SetPriority</span><span class="sxs-lookup"><span data-stu-id="939d7-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="939d7-116">Solicitações que o host de ajustar a prioridade do thread de nível para a tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="939d7-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="939d7-117">Método Start</span><span class="sxs-lookup"><span data-stu-id="939d7-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="939d7-118">Solicitações que o host de move a tarefa representada por atual `IHostTask` instância de um estado suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="939d7-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="939d7-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="939d7-119">Remarks</span></span>  
 <span data-ttu-id="939d7-120">O CLR chama os métodos definidos pela `IHostTask` para iniciar uma tarefa, defina sua prioridade de thread, nível, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="939d7-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="939d7-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="939d7-121">Requirements</span></span>  
 <span data-ttu-id="939d7-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="939d7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="939d7-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="939d7-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="939d7-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="939d7-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="939d7-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="939d7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939d7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="939d7-126">See also</span></span>

- [<span data-ttu-id="939d7-127">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="939d7-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="939d7-128">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="939d7-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="939d7-129">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="939d7-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="939d7-130">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="939d7-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
