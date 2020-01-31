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
ms.openlocfilehash: d6c923f03309da3ad8092ea6119e7d850120ee2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783800"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="4661f-102">Interface ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="4661f-102">ICorDebugController Interface</span></span>

<span data-ttu-id="4661f-103">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="4661f-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4661f-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4661f-104">Methods</span></span>  
  
|<span data-ttu-id="4661f-105">Método</span><span class="sxs-lookup"><span data-stu-id="4661f-105">Method</span></span>|<span data-ttu-id="4661f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4661f-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="4661f-107">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="4661f-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="4661f-108">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="4661f-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="4661f-109">Método continue</span><span class="sxs-lookup"><span data-stu-id="4661f-109">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="4661f-110">Retoma a execução de threads gerenciados após uma chamada para [ICorDebugController:: Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="4661f-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="4661f-111">Método Detach</span><span class="sxs-lookup"><span data-stu-id="4661f-111">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="4661f-112">Desanexa o depurador do domínio do processo ou do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4661f-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="4661f-113">Método EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="4661f-113">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="4661f-114">Obtém um enumerador para os threads gerenciados ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="4661f-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="4661f-115">Método HasQueuedCallbacks</span><span class="sxs-lookup"><span data-stu-id="4661f-115">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="4661f-116">Obtém um valor que indica se qualquer retorno de chamada gerenciado está na fila no momento para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="4661f-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="4661f-117">Método IsRunning</span><span class="sxs-lookup"><span data-stu-id="4661f-117">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="4661f-118">Obtém um valor que indica se os threads no processo estão em execução livremente no momento.</span><span class="sxs-lookup"><span data-stu-id="4661f-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="4661f-119">Método SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="4661f-119">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="4661f-120">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="4661f-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="4661f-121">Método Stop</span><span class="sxs-lookup"><span data-stu-id="4661f-121">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="4661f-122">Executa uma parada cooperativa em todos os threads que estão executando código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="4661f-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="4661f-123">Método Terminate</span><span class="sxs-lookup"><span data-stu-id="4661f-123">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="4661f-124">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="4661f-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4661f-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="4661f-125">Remarks</span></span>  
 <span data-ttu-id="4661f-126">Se `ICorDebugController` estiver controlando um processo, o escopo incluirá todos os threads do processo.</span><span class="sxs-lookup"><span data-stu-id="4661f-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="4661f-127">Se `ICorDebugController` estiver controlando um domínio de aplicativo, o escopo incluirá somente os threads desse domínio de aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="4661f-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4661f-128">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="4661f-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4661f-129">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4661f-129">Requirements</span></span>  
 <span data-ttu-id="4661f-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4661f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4661f-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4661f-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4661f-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4661f-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4661f-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4661f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4661f-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="4661f-134">See also</span></span>

- [<span data-ttu-id="4661f-135">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4661f-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
