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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7628aa0ad10398f92d475c4c776810e13fac22b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749495"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="86a1a-102">Interface ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="86a1a-102">ICorDebugController Interface</span></span>

<span data-ttu-id="86a1a-103">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="86a1a-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86a1a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="86a1a-104">Methods</span></span>  
  
|<span data-ttu-id="86a1a-105">Método</span><span class="sxs-lookup"><span data-stu-id="86a1a-105">Method</span></span>|<span data-ttu-id="86a1a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="86a1a-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="86a1a-107">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="86a1a-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="86a1a-108">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="86a1a-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="86a1a-109">Método continue</span><span class="sxs-lookup"><span data-stu-id="86a1a-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="86a1a-110">Retoma a execução de threads gerenciados após uma chamada para [icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="86a1a-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="86a1a-111">Método Detach</span><span class="sxs-lookup"><span data-stu-id="86a1a-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="86a1a-112">Desanexa o depurador do domínio de aplicativo ou processo.</span><span class="sxs-lookup"><span data-stu-id="86a1a-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="86a1a-113">Método EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="86a1a-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="86a1a-114">Obtém um enumerador para os Active Directory threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="86a1a-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="86a1a-115">Método HasQueuedCallbacks</span><span class="sxs-lookup"><span data-stu-id="86a1a-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="86a1a-116">Obtém um valor que indica se qualquer retorno de chamada gerenciado atualmente na fila para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="86a1a-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="86a1a-117">Método IsRunning</span><span class="sxs-lookup"><span data-stu-id="86a1a-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="86a1a-118">Obtém um valor que indica se os threads no processo estão atualmente em execução livremente.</span><span class="sxs-lookup"><span data-stu-id="86a1a-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="86a1a-119">Método SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="86a1a-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="86a1a-120">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="86a1a-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="86a1a-121">Método Stop</span><span class="sxs-lookup"><span data-stu-id="86a1a-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="86a1a-122">Executa uma parada cooperativa em todos os threads que estão executando o código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="86a1a-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="86a1a-123">Método Terminate</span><span class="sxs-lookup"><span data-stu-id="86a1a-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="86a1a-124">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="86a1a-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86a1a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="86a1a-125">Remarks</span></span>  
 <span data-ttu-id="86a1a-126">Se `ICorDebugController` está controlando um processo, o escopo inclui todos os threads do processo.</span><span class="sxs-lookup"><span data-stu-id="86a1a-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="86a1a-127">Se `ICorDebugController` é controlar a um domínio de aplicativo, o escopo inclui apenas os threads desse domínio de aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="86a1a-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86a1a-128">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="86a1a-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a1a-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86a1a-129">Requirements</span></span>  
 <span data-ttu-id="86a1a-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a1a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a1a-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86a1a-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a1a-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86a1a-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86a1a-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a1a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a1a-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86a1a-134">See also</span></span>

- [<span data-ttu-id="86a1a-135">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="86a1a-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
