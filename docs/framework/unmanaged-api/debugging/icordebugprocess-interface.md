---
title: ICorDebugProcess Interface1
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
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6fa95d17e7ff6f857765ea2dd48f61b047a47b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="924e4-102">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="924e4-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="924e4-103">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="924e4-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="924e4-104">Esta interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="924e4-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="924e4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="924e4-105">Methods</span></span>  
  
|<span data-ttu-id="924e4-106">Método</span><span class="sxs-lookup"><span data-stu-id="924e4-106">Method</span></span>|<span data-ttu-id="924e4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="924e4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="924e4-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="924e4-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="924e4-109">Limpa a exceção atual não gerenciada em um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="924e4-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="924e4-110">Método EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="924e4-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="924e4-111">Habilita e desabilita o envio de mensagens de log para o depurador.</span><span class="sxs-lookup"><span data-stu-id="924e4-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="924e4-112">Método EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="924e4-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="924e4-113">Enumera todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="924e4-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="924e4-114">Método EnumerateObjects</span><span class="sxs-lookup"><span data-stu-id="924e4-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="924e4-115">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="924e4-115">Not implemented.</span></span>|  
|[<span data-ttu-id="924e4-116">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="924e4-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="924e4-117">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="924e4-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="924e4-118">Método GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="924e4-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="924e4-119">Obtém a ID do thread de sistema operacional (SO) para o thread de auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="924e4-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="924e4-120">Método GetID</span><span class="sxs-lookup"><span data-stu-id="924e4-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="924e4-121">Obtém a ID de sistema operacional (SO) do processo.</span><span class="sxs-lookup"><span data-stu-id="924e4-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="924e4-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="924e4-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="924e4-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="924e4-123">Not implemented.</span></span>|  
|[<span data-ttu-id="924e4-124">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="924e4-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="924e4-125">Obtém a instância de ICorDebugThread que tem o thread de sistema operacional especificado ID</span><span class="sxs-lookup"><span data-stu-id="924e4-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="924e4-126">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="924e4-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="924e4-127">Obtém o contexto do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="924e4-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="924e4-128">Método IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="924e4-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="924e4-129">Determina se o thread foi suspenso como resultado o depurador ao interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="924e4-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="924e4-130">Método IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="924e4-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="924e4-131">Determina se um endereço está dentro de um stub que fará com que uma transição para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="924e4-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="924e4-132">Método ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="924e4-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="924e4-133">Define o nível de severidade da opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="924e4-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="924e4-134">Método ReadMemory</span><span class="sxs-lookup"><span data-stu-id="924e4-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="924e4-135">Ler a memória do processo.</span><span class="sxs-lookup"><span data-stu-id="924e4-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="924e4-136">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="924e4-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="924e4-137">Define o contexto de determinado thread.</span><span class="sxs-lookup"><span data-stu-id="924e4-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="924e4-138">Método ThreadForFiberCookie</span><span class="sxs-lookup"><span data-stu-id="924e4-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="924e4-139">Preterido.</span><span class="sxs-lookup"><span data-stu-id="924e4-139">Deprecated.</span></span>|  
|[<span data-ttu-id="924e4-140">Método WriteMemory</span><span class="sxs-lookup"><span data-stu-id="924e4-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="924e4-141">Grava dados em uma área da memória do processo.</span><span class="sxs-lookup"><span data-stu-id="924e4-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="924e4-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="924e4-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="924e4-143">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="924e4-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="924e4-144">Requisitos</span><span class="sxs-lookup"><span data-stu-id="924e4-144">Requirements</span></span>  
 <span data-ttu-id="924e4-145">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="924e4-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="924e4-146">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="924e4-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="924e4-147">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="924e4-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="924e4-148">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="924e4-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924e4-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="924e4-149">See Also</span></span>  
 [<span data-ttu-id="924e4-150">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="924e4-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="924e4-151">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="924e4-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
