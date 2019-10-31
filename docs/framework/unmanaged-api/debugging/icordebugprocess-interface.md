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
ms.openlocfilehash: 393ac8c119f111b645e7ccdb6ea94efee7207fa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128789"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="85b16-102">Interface ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="85b16-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="85b16-103">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="85b16-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="85b16-104">Essa interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="85b16-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85b16-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="85b16-105">Methods</span></span>  
  
|<span data-ttu-id="85b16-106">Método</span><span class="sxs-lookup"><span data-stu-id="85b16-106">Method</span></span>|<span data-ttu-id="85b16-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="85b16-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85b16-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="85b16-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="85b16-109">Limpa a exceção não gerenciada atual no thread determinado.</span><span class="sxs-lookup"><span data-stu-id="85b16-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="85b16-110">Método EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="85b16-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="85b16-111">Habilita e desabilita o envio de mensagens de log para o depurador.</span><span class="sxs-lookup"><span data-stu-id="85b16-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="85b16-112">Método EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="85b16-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="85b16-113">Enumera todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="85b16-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="85b16-114">Método EnumerateObjects</span><span class="sxs-lookup"><span data-stu-id="85b16-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="85b16-115">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="85b16-115">Not implemented.</span></span>|  
|[<span data-ttu-id="85b16-116">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="85b16-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="85b16-117">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="85b16-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="85b16-118">Método GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="85b16-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="85b16-119">Obtém a ID do thread do sistema operacional (SO) para o thread auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="85b16-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="85b16-120">Método GetID</span><span class="sxs-lookup"><span data-stu-id="85b16-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="85b16-121">Obtém a ID do sistema operacional (SO) do processo.</span><span class="sxs-lookup"><span data-stu-id="85b16-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="85b16-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="85b16-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="85b16-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="85b16-123">Not implemented.</span></span>|  
|[<span data-ttu-id="85b16-124">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="85b16-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="85b16-125">Obtém a instância ICorDebugThread que tem a ID de thread do sistema operacional especificada.</span><span class="sxs-lookup"><span data-stu-id="85b16-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="85b16-126">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="85b16-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="85b16-127">Obtém o contexto para o thread fornecido.</span><span class="sxs-lookup"><span data-stu-id="85b16-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="85b16-128">Método IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="85b16-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="85b16-129">Determina se o thread foi suspenso como resultado do depurador parando o processo.</span><span class="sxs-lookup"><span data-stu-id="85b16-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="85b16-130">Método IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="85b16-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="85b16-131">Determina se um endereço está dentro de um stub que causará uma transição para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="85b16-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="85b16-132">Método ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="85b16-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="85b16-133">Define o nível de severidade da opção de log especificada.</span><span class="sxs-lookup"><span data-stu-id="85b16-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="85b16-134">Método ReadMemory</span><span class="sxs-lookup"><span data-stu-id="85b16-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="85b16-135">Lê a memória do processo.</span><span class="sxs-lookup"><span data-stu-id="85b16-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="85b16-136">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="85b16-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="85b16-137">Define o contexto para o thread fornecido.</span><span class="sxs-lookup"><span data-stu-id="85b16-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="85b16-138">Método ThreadForFiberCookie</span><span class="sxs-lookup"><span data-stu-id="85b16-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="85b16-139">Preterido.</span><span class="sxs-lookup"><span data-stu-id="85b16-139">Deprecated.</span></span>|  
|[<span data-ttu-id="85b16-140">Método WriteMemory</span><span class="sxs-lookup"><span data-stu-id="85b16-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="85b16-141">Grava dados em uma área de memória no processo.</span><span class="sxs-lookup"><span data-stu-id="85b16-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85b16-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="85b16-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85b16-143">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="85b16-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85b16-144">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85b16-144">Requirements</span></span>  
 <span data-ttu-id="85b16-145">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85b16-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85b16-146">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85b16-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85b16-147">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85b16-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85b16-148">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85b16-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b16-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85b16-149">See also</span></span>

- [<span data-ttu-id="85b16-150">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="85b16-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="85b16-151">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="85b16-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
