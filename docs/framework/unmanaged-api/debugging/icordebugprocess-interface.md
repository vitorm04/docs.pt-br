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
ms.openlocfilehash: 46d96d66f16cd956d8fab1afe00486d564e37953
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216789"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="1fb8f-102">Interface ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="1fb8f-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="1fb8f-103">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="1fb8f-104">Essa interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1fb8f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1fb8f-105">Methods</span></span>  
  
|<span data-ttu-id="1fb8f-106">Método</span><span class="sxs-lookup"><span data-stu-id="1fb8f-106">Method</span></span>|<span data-ttu-id="1fb8f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fb8f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1fb8f-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="1fb8f-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="1fb8f-109">Limpa a exceção atual não gerenciada em um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="1fb8f-110">Método EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="1fb8f-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="1fb8f-111">Habilita e desabilita o envio de mensagens de log para o depurador.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="1fb8f-112">Método EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="1fb8f-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="1fb8f-113">Enumera todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="1fb8f-114">Método EnumerateObjects</span><span class="sxs-lookup"><span data-stu-id="1fb8f-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="1fb8f-115">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-115">Not implemented.</span></span>|  
|[<span data-ttu-id="1fb8f-116">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="1fb8f-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="1fb8f-117">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="1fb8f-118">Método GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="1fb8f-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="1fb8f-119">Obtém a ID do thread de sistema operacional (SO) para o thread de auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="1fb8f-120">Método GetID</span><span class="sxs-lookup"><span data-stu-id="1fb8f-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="1fb8f-121">Obtém a ID do sistema operacional (SO) do processo.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="1fb8f-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="1fb8f-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="1fb8f-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-123">Not implemented.</span></span>|  
|[<span data-ttu-id="1fb8f-124">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="1fb8f-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="1fb8f-125">ID do obtém a instância de ICorDebugThread que tem o thread de sistema operacional especificado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="1fb8f-126">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="1fb8f-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="1fb8f-127">Obtém o contexto para o thread determinado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1fb8f-128">Método IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="1fb8f-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="1fb8f-129">Determina se o thread foi suspenso como resultado o depurador interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="1fb8f-130">Método IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="1fb8f-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="1fb8f-131">Determina se um endereço é dentro de um stub que fará com que uma transição para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="1fb8f-132">Método ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="1fb8f-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="1fb8f-133">Define o nível de severidade da opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="1fb8f-134">Método ReadMemory</span><span class="sxs-lookup"><span data-stu-id="1fb8f-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="1fb8f-135">Lê a memória do processo.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="1fb8f-136">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="1fb8f-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="1fb8f-137">Define o contexto para o thread determinado.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1fb8f-138">Método ThreadForFiberCookie</span><span class="sxs-lookup"><span data-stu-id="1fb8f-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="1fb8f-139">Preterido.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-139">Deprecated.</span></span>|  
|[<span data-ttu-id="1fb8f-140">Método WriteMemory</span><span class="sxs-lookup"><span data-stu-id="1fb8f-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="1fb8f-141">Grava dados em uma área da memória no processo.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fb8f-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="1fb8f-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb8f-143">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fb8f-144">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1fb8f-144">Requirements</span></span>  
 <span data-ttu-id="1fb8f-145">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fb8f-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fb8f-146">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fb8f-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fb8f-147">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fb8f-147">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1fb8f-148">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1fb8f-148">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1fb8f-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fb8f-149">See also</span></span>

- [<span data-ttu-id="1fb8f-150">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1fb8f-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="1fb8f-151">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1fb8f-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
