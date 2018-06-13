---
title: ICorDebugProcess Interface1
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
ms.openlocfilehash: 06e4e3854a850c9639e93c8db2ec8ccd567b242b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423163"
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="5e3ff-102">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="5e3ff-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="5e3ff-103">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="5e3ff-104">Esta interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e3ff-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5e3ff-105">Methods</span></span>  
  
|<span data-ttu-id="5e3ff-106">Método</span><span class="sxs-lookup"><span data-stu-id="5e3ff-106">Method</span></span>|<span data-ttu-id="5e3ff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e3ff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e3ff-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="5e3ff-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="5e3ff-109">Limpa a exceção atual não gerenciada em um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="5e3ff-110">Método EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="5e3ff-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="5e3ff-111">Habilita e desabilita o envio de mensagens de log para o depurador.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="5e3ff-112">Método EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="5e3ff-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="5e3ff-113">Enumera todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="5e3ff-114">Método EnumerateObjects</span><span class="sxs-lookup"><span data-stu-id="5e3ff-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="5e3ff-115">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-115">Not implemented.</span></span>|  
|[<span data-ttu-id="5e3ff-116">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="5e3ff-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="5e3ff-117">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="5e3ff-118">Método GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="5e3ff-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="5e3ff-119">Obtém a ID do thread de sistema operacional (SO) para o thread de auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="5e3ff-120">Método GetID</span><span class="sxs-lookup"><span data-stu-id="5e3ff-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="5e3ff-121">Obtém a ID de sistema operacional (SO) do processo.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="5e3ff-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="5e3ff-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="5e3ff-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-123">Not implemented.</span></span>|  
|[<span data-ttu-id="5e3ff-124">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="5e3ff-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="5e3ff-125">Obtém a instância de ICorDebugThread que tem o thread de sistema operacional especificado ID</span><span class="sxs-lookup"><span data-stu-id="5e3ff-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="5e3ff-126">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="5e3ff-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="5e3ff-127">Obtém o contexto do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="5e3ff-128">Método IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="5e3ff-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="5e3ff-129">Determina se o thread foi suspenso como resultado o depurador ao interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="5e3ff-130">Método IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="5e3ff-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="5e3ff-131">Determina se um endereço está dentro de um stub que fará com que uma transição para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="5e3ff-132">Método ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="5e3ff-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="5e3ff-133">Define o nível de severidade da opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="5e3ff-134">Método ReadMemory</span><span class="sxs-lookup"><span data-stu-id="5e3ff-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="5e3ff-135">Ler a memória do processo.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="5e3ff-136">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="5e3ff-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="5e3ff-137">Define o contexto de determinado thread.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="5e3ff-138">Método ThreadForFiberCookie</span><span class="sxs-lookup"><span data-stu-id="5e3ff-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="5e3ff-139">Preterido.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-139">Deprecated.</span></span>|  
|[<span data-ttu-id="5e3ff-140">Método WriteMemory</span><span class="sxs-lookup"><span data-stu-id="5e3ff-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="5e3ff-141">Grava dados em uma área da memória do processo.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e3ff-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e3ff-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e3ff-143">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="5e3ff-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e3ff-144">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e3ff-144">Requirements</span></span>  
 <span data-ttu-id="5e3ff-145">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e3ff-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e3ff-146">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e3ff-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e3ff-147">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e3ff-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e3ff-148">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e3ff-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3ff-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e3ff-149">See Also</span></span>  
 [<span data-ttu-id="5e3ff-150">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="5e3ff-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="5e3ff-151">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5e3ff-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
