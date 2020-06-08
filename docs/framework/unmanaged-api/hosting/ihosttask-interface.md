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
ms.openlocfilehash: 1b7209a36f8e9d6f02bd4cc1882adeef8af30c3d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503910"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="31d3a-102">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="31d3a-102">IHostTask Interface</span></span>
<span data-ttu-id="31d3a-103">Fornece métodos que permitem que o Common Language Runtime (CLR) se comunique com o host para gerenciar tarefas.</span><span class="sxs-lookup"><span data-stu-id="31d3a-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31d3a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="31d3a-104">Methods</span></span>  
  
|<span data-ttu-id="31d3a-105">Método</span><span class="sxs-lookup"><span data-stu-id="31d3a-105">Method</span></span>|<span data-ttu-id="31d3a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="31d3a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31d3a-107">Método Alert</span><span class="sxs-lookup"><span data-stu-id="31d3a-107">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="31d3a-108">Solicita que o host ative a tarefa representada pela instância atual `IHostTask` , para que a tarefa possa ser anulada.</span><span class="sxs-lookup"><span data-stu-id="31d3a-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="31d3a-109">Método GetPriority</span><span class="sxs-lookup"><span data-stu-id="31d3a-109">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="31d3a-110">Obtém o nível de prioridade do thread da tarefa representada pela `IHostTask` instância atual.</span><span class="sxs-lookup"><span data-stu-id="31d3a-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="31d3a-111">Método Join</span><span class="sxs-lookup"><span data-stu-id="31d3a-111">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="31d3a-112">Bloqueia a tarefa de chamada até que a tarefa representada pela `IHostTask` instância atual seja concluída, o intervalo de tempo especificado decorre ou [IHostTask:: Alert](ihosttask-alert-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="31d3a-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="31d3a-113">Método SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="31d3a-113">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="31d3a-114">Associa uma instância de [interface ICLRTask](iclrtask-interface.md) à `IHostTask` instância atual.</span><span class="sxs-lookup"><span data-stu-id="31d3a-114">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="31d3a-115">Método SetPriority</span><span class="sxs-lookup"><span data-stu-id="31d3a-115">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="31d3a-116">Solicita que o host ajuste o nível de prioridade de thread para a tarefa representada pela `IHostTask` instância atual.</span><span class="sxs-lookup"><span data-stu-id="31d3a-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="31d3a-117">Método de início</span><span class="sxs-lookup"><span data-stu-id="31d3a-117">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="31d3a-118">Solicita que o host mova a tarefa representada pela instância atual `IHostTask` de um estado suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="31d3a-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31d3a-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="31d3a-119">Remarks</span></span>  
 <span data-ttu-id="31d3a-120">O CLR chama os métodos definidos pelo `IHostTask` para iniciar uma tarefa, definir seu nível de prioridade de thread e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="31d3a-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d3a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31d3a-121">Requirements</span></span>  
 <span data-ttu-id="31d3a-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d3a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d3a-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31d3a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31d3a-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31d3a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31d3a-125">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d3a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d3a-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="31d3a-126">See also</span></span>

- [<span data-ttu-id="31d3a-127">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="31d3a-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="31d3a-128">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="31d3a-128">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="31d3a-129">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="31d3a-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="31d3a-130">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="31d3a-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
