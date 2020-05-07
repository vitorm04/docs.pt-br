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
ms.openlocfilehash: e494bbb24e8f2245593e7945625e72e70ae1dde5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892769"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="f615a-102">Interface ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="f615a-102">ICorDebugController Interface</span></span>

<span data-ttu-id="f615a-103">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="f615a-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f615a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f615a-104">Methods</span></span>  
  
|<span data-ttu-id="f615a-105">Método</span><span class="sxs-lookup"><span data-stu-id="f615a-105">Method</span></span>|<span data-ttu-id="f615a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f615a-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="f615a-107">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f615a-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="f615a-108">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f615a-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="f615a-109">Método Continue</span><span class="sxs-lookup"><span data-stu-id="f615a-109">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="f615a-110">Retoma a execução de threads gerenciados após uma chamada para [ICorDebugController:: Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="f615a-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="f615a-111">Método Detach</span><span class="sxs-lookup"><span data-stu-id="f615a-111">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="f615a-112">Desanexa o depurador do domínio do processo ou do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f615a-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="f615a-113">Método EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="f615a-113">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="f615a-114">Obtém um enumerador para os threads gerenciados ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="f615a-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="f615a-115">Método HasQueuedCallbacks</span><span class="sxs-lookup"><span data-stu-id="f615a-115">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="f615a-116">Obtém um valor que indica se qualquer retorno de chamada gerenciado está na fila no momento para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="f615a-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="f615a-117">Método IsRunning</span><span class="sxs-lookup"><span data-stu-id="f615a-117">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="f615a-118">Obtém um valor que indica se os threads no processo estão em execução livremente no momento.</span><span class="sxs-lookup"><span data-stu-id="f615a-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="f615a-119">Método SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="f615a-119">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="f615a-120">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="f615a-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="f615a-121">Método Stop</span><span class="sxs-lookup"><span data-stu-id="f615a-121">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="f615a-122">Executa uma parada cooperativa em todos os threads que estão executando código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="f615a-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="f615a-123">Método Terminate</span><span class="sxs-lookup"><span data-stu-id="f615a-123">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="f615a-124">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="f615a-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f615a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="f615a-125">Remarks</span></span>  
 <span data-ttu-id="f615a-126">Se `ICorDebugController` o estiver controlando um processo, o escopo incluirá todos os threads do processo.</span><span class="sxs-lookup"><span data-stu-id="f615a-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="f615a-127">Se `ICorDebugController` o estiver controlando um domínio de aplicativo, o escopo incluirá somente os threads desse domínio de aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="f615a-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f615a-128">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="f615a-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f615a-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f615a-129">Requirements</span></span>  
 <span data-ttu-id="f615a-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f615a-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f615a-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f615a-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f615a-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f615a-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f615a-133">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f615a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f615a-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f615a-134">See also</span></span>

- [<span data-ttu-id="f615a-135">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f615a-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
