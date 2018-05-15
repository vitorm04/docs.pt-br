---
title: ICorDebugController Interface1
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
ms.openlocfilehash: 230488201b637c5a53f41dd4c3f204b37e8984fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="8b89f-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="8b89f-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="8b89f-103">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="8b89f-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b89f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8b89f-104">Methods</span></span>  
  
|<span data-ttu-id="8b89f-105">Método</span><span class="sxs-lookup"><span data-stu-id="8b89f-105">Method</span></span>|<span data-ttu-id="8b89f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b89f-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="8b89f-107">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="8b89f-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="8b89f-108">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="8b89f-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="8b89f-109">Método continue</span><span class="sxs-lookup"><span data-stu-id="8b89f-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="8b89f-110">Retoma a execução de threads gerenciados após uma chamada para [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="8b89f-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="8b89f-111">Método Detach</span><span class="sxs-lookup"><span data-stu-id="8b89f-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="8b89f-112">Desanexa o depurador do domínio de aplicativo ou processo.</span><span class="sxs-lookup"><span data-stu-id="8b89f-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="8b89f-113">Método EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="8b89f-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="8b89f-114">Obtém um enumerador para os threads gerenciados ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="8b89f-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="8b89f-115">Método HasQueuedCallbacks</span><span class="sxs-lookup"><span data-stu-id="8b89f-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="8b89f-116">Obtém um valor que indica se qualquer retornos de chamada gerenciados atualmente na fila para o segmento especificado.</span><span class="sxs-lookup"><span data-stu-id="8b89f-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="8b89f-117">Método IsRunning</span><span class="sxs-lookup"><span data-stu-id="8b89f-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="8b89f-118">Obtém um valor que indica se os threads do processo estão em execução no momento livremente.</span><span class="sxs-lookup"><span data-stu-id="8b89f-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="8b89f-119">Método SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="8b89f-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="8b89f-120">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="8b89f-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="8b89f-121">Método Stop</span><span class="sxs-lookup"><span data-stu-id="8b89f-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="8b89f-122">Executa uma parada cooperativa em todos os threads que estão executando o código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="8b89f-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="8b89f-123">Método Terminate</span><span class="sxs-lookup"><span data-stu-id="8b89f-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="8b89f-124">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="8b89f-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b89f-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b89f-125">Remarks</span></span>  
 <span data-ttu-id="8b89f-126">Se `ICorDebugController` é controlar um processo, o escopo inclui todos os threads do processo.</span><span class="sxs-lookup"><span data-stu-id="8b89f-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="8b89f-127">Se `ICorDebugController` está controlando a um domínio de aplicativo, o escopo inclui apenas os segmentos de domínio de aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="8b89f-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b89f-128">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="8b89f-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b89f-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b89f-129">Requirements</span></span>  
 <span data-ttu-id="8b89f-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b89f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b89f-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b89f-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b89f-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b89f-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b89f-133">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b89f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b89f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b89f-134">See Also</span></span>  
 [<span data-ttu-id="8b89f-135">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8b89f-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
