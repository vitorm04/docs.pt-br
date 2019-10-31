---
title: Interface ICorDebugController
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 27f991c12ea7786d6146b5731848ca5ad3a37e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125364"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="d2584-102">Interface ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="d2584-102">ICorDebugController Interface</span></span>

<span data-ttu-id="d2584-103">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="d2584-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2584-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d2584-104">Methods</span></span>  
  
|<span data-ttu-id="d2584-105">Método</span><span class="sxs-lookup"><span data-stu-id="d2584-105">Method</span></span>|<span data-ttu-id="d2584-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2584-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="d2584-107">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d2584-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="d2584-108">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d2584-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="d2584-109">Método continue</span><span class="sxs-lookup"><span data-stu-id="d2584-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="d2584-110">Retoma a execução de threads gerenciados após uma chamada para [ICorDebugController:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="d2584-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="d2584-111">Método Detach</span><span class="sxs-lookup"><span data-stu-id="d2584-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="d2584-112">Desanexa o depurador do domínio do processo ou do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2584-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="d2584-113">Método EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="d2584-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="d2584-114">Obtém um enumerador para os threads gerenciados ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="d2584-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="d2584-115">Método HasQueuedCallbacks</span><span class="sxs-lookup"><span data-stu-id="d2584-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="d2584-116">Obtém um valor que indica se qualquer retorno de chamada gerenciado está na fila no momento para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="d2584-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="d2584-117">Método IsRunning</span><span class="sxs-lookup"><span data-stu-id="d2584-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="d2584-118">Obtém um valor que indica se os threads no processo estão em execução livremente no momento.</span><span class="sxs-lookup"><span data-stu-id="d2584-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="d2584-119">Método SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="d2584-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="d2584-120">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="d2584-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="d2584-121">Método Stop</span><span class="sxs-lookup"><span data-stu-id="d2584-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="d2584-122">Executa uma parada cooperativa em todos os threads que estão executando código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="d2584-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="d2584-123">Método Terminate</span><span class="sxs-lookup"><span data-stu-id="d2584-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="d2584-124">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="d2584-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2584-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2584-125">Remarks</span></span>  
 <span data-ttu-id="d2584-126">Se `ICorDebugController` estiver controlando um processo, o escopo incluirá todos os threads do processo.</span><span class="sxs-lookup"><span data-stu-id="d2584-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="d2584-127">Se `ICorDebugController` estiver controlando um domínio de aplicativo, o escopo incluirá somente os threads desse domínio de aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="d2584-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2584-128">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="d2584-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2584-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2584-129">Requirements</span></span>  
 <span data-ttu-id="d2584-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2584-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2584-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2584-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2584-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2584-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2584-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2584-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2584-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2584-134">See also</span></span>

- [<span data-ttu-id="d2584-135">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d2584-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
