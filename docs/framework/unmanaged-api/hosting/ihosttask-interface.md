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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121388"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="3d51f-102">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="3d51f-102">IHostTask Interface</span></span>
<span data-ttu-id="3d51f-103">Fornece métodos que permitem que o Common Language Runtime (CLR) se comunique com o host para gerenciar tarefas.</span><span class="sxs-lookup"><span data-stu-id="3d51f-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d51f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3d51f-104">Methods</span></span>  
  
|<span data-ttu-id="3d51f-105">Método</span><span class="sxs-lookup"><span data-stu-id="3d51f-105">Method</span></span>|<span data-ttu-id="3d51f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d51f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d51f-107">Método Alert</span><span class="sxs-lookup"><span data-stu-id="3d51f-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="3d51f-108">Solicita que o host ative a tarefa representada pela instância de `IHostTask` atual, para que a tarefa possa ser anulada.</span><span class="sxs-lookup"><span data-stu-id="3d51f-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="3d51f-109">Método GetPriority</span><span class="sxs-lookup"><span data-stu-id="3d51f-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="3d51f-110">Obtém o nível de prioridade de thread da tarefa representada pela instância de `IHostTask` atual.</span><span class="sxs-lookup"><span data-stu-id="3d51f-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="3d51f-111">Método Join</span><span class="sxs-lookup"><span data-stu-id="3d51f-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="3d51f-112">Bloqueia a tarefa de chamada até que a tarefa representada pela instância de `IHostTask` atual seja concluída, o intervalo de tempo especificado decorre ou [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="3d51f-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="3d51f-113">Método SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="3d51f-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="3d51f-114">Associa uma instância de [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) com a instância de `IHostTask` atual.</span><span class="sxs-lookup"><span data-stu-id="3d51f-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="3d51f-115">Método SetPriority</span><span class="sxs-lookup"><span data-stu-id="3d51f-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="3d51f-116">Solicita que o host ajuste o nível de prioridade de thread para a tarefa representada pela instância de `IHostTask` atual.</span><span class="sxs-lookup"><span data-stu-id="3d51f-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="3d51f-117">Método Start</span><span class="sxs-lookup"><span data-stu-id="3d51f-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="3d51f-118">Solicita que o host mova a tarefa representada pela instância de `IHostTask` atual de um estado suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="3d51f-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d51f-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d51f-119">Remarks</span></span>  
 <span data-ttu-id="3d51f-120">O CLR chama os métodos definidos por `IHostTask` para iniciar uma tarefa, definir seu nível de prioridade de thread e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="3d51f-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d51f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d51f-121">Requirements</span></span>  
 <span data-ttu-id="3d51f-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d51f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d51f-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3d51f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d51f-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3d51f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d51f-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d51f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d51f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d51f-126">See also</span></span>

- [<span data-ttu-id="3d51f-127">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3d51f-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3d51f-128">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3d51f-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3d51f-129">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3d51f-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="3d51f-130">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="3d51f-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
