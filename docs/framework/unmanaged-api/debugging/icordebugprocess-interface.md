---
title: Interface ICorDebugProcess
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b99630ba60cd84254024b91dba9ef9922fd7e041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943312"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="f8693-102">Interface ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="f8693-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="f8693-103">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f8693-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="f8693-104">Essa interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="f8693-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8693-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f8693-105">Methods</span></span>  
  
|<span data-ttu-id="f8693-106">Método</span><span class="sxs-lookup"><span data-stu-id="f8693-106">Method</span></span>|<span data-ttu-id="f8693-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8693-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8693-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="f8693-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="f8693-109">Limpa a exceção não gerenciada atual no thread determinado.</span><span class="sxs-lookup"><span data-stu-id="f8693-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="f8693-110">Método EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="f8693-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="f8693-111">Habilita e desabilita o envio de mensagens de log para o depurador.</span><span class="sxs-lookup"><span data-stu-id="f8693-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="f8693-112">Método EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="f8693-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="f8693-113">Enumera todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="f8693-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="f8693-114">Método EnumerateObjects</span><span class="sxs-lookup"><span data-stu-id="f8693-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="f8693-115">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="f8693-115">Not implemented.</span></span>|  
|[<span data-ttu-id="f8693-116">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="f8693-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="f8693-117">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="f8693-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="f8693-118">Método GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="f8693-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="f8693-119">Obtém a ID do thread do sistema operacional (SO) para o thread auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="f8693-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="f8693-120">Método GetID</span><span class="sxs-lookup"><span data-stu-id="f8693-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="f8693-121">Obtém a ID do sistema operacional (SO) do processo.</span><span class="sxs-lookup"><span data-stu-id="f8693-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="f8693-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="f8693-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="f8693-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="f8693-123">Not implemented.</span></span>|  
|[<span data-ttu-id="f8693-124">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="f8693-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="f8693-125">Obtém a instância ICorDebugThread que tem a ID de thread do sistema operacional especificada.</span><span class="sxs-lookup"><span data-stu-id="f8693-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="f8693-126">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="f8693-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="f8693-127">Obtém o contexto para o thread fornecido.</span><span class="sxs-lookup"><span data-stu-id="f8693-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="f8693-128">Método IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="f8693-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="f8693-129">Determina se o thread foi suspenso como resultado do depurador parando o processo.</span><span class="sxs-lookup"><span data-stu-id="f8693-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="f8693-130">Método IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="f8693-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="f8693-131">Determina se um endereço está dentro de um stub que causará uma transição para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f8693-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="f8693-132">Método ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="f8693-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="f8693-133">Define o nível de severidade da opção de log especificada.</span><span class="sxs-lookup"><span data-stu-id="f8693-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="f8693-134">Método ReadMemory</span><span class="sxs-lookup"><span data-stu-id="f8693-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="f8693-135">Lê a memória do processo.</span><span class="sxs-lookup"><span data-stu-id="f8693-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="f8693-136">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="f8693-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="f8693-137">Define o contexto para o thread fornecido.</span><span class="sxs-lookup"><span data-stu-id="f8693-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="f8693-138">Método ThreadForFiberCookie</span><span class="sxs-lookup"><span data-stu-id="f8693-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="f8693-139">Preterido.</span><span class="sxs-lookup"><span data-stu-id="f8693-139">Deprecated.</span></span>|  
|[<span data-ttu-id="f8693-140">Método WriteMemory</span><span class="sxs-lookup"><span data-stu-id="f8693-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="f8693-141">Grava dados em uma área de memória no processo.</span><span class="sxs-lookup"><span data-stu-id="f8693-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8693-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8693-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8693-143">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="f8693-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8693-144">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8693-144">Requirements</span></span>  
 <span data-ttu-id="f8693-145">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8693-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8693-146">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8693-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8693-147">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8693-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8693-148">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8693-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8693-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8693-149">See also</span></span>

- [<span data-ttu-id="f8693-150">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="f8693-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="f8693-151">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f8693-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
