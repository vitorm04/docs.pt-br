---
title: Interface ICorDebugThread
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f2223230b18f175427bfbfeaa46bf1406d8c7e5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976350"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="3526b-102">Interface ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="3526b-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="3526b-103">Representa um thread em um processo.</span><span class="sxs-lookup"><span data-stu-id="3526b-103">Represents a thread in a process.</span></span> <span data-ttu-id="3526b-104">O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.</span><span class="sxs-lookup"><span data-stu-id="3526b-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3526b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3526b-105">Methods</span></span>  
  
|<span data-ttu-id="3526b-106">Método</span><span class="sxs-lookup"><span data-stu-id="3526b-106">Method</span></span>|<span data-ttu-id="3526b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3526b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3526b-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="3526b-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="3526b-109">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="3526b-109">This method is not implemented.</span></span> <span data-ttu-id="3526b-110">Não o use.</span><span class="sxs-lookup"><span data-stu-id="3526b-110">Do not use it.</span></span>|  
|[<span data-ttu-id="3526b-111">Método CreateEval</span><span class="sxs-lookup"><span data-stu-id="3526b-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="3526b-112">Cria um objeto de ICorDebugEval que opera sobre isso `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-113">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="3526b-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="3526b-114">Cria um objeto de ICorDebugStepper que permite percorrer o quadro ativo neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-115">Método EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="3526b-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="3526b-116">Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-117">Método GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="3526b-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="3526b-118">Obtém um ponteiro de interface para o Active Directory ICorDebugChain neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-119">Método GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="3526b-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="3526b-120">Obtém um ponteiro de interface para o Active Directory ICorDebugFrame neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-121">Método GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="3526b-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="3526b-122">Obtém um ponteiro de interface para o domínio do aplicativo no qual este `ICorDebugThread` está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="3526b-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="3526b-123">Método GetCurrentException</span><span class="sxs-lookup"><span data-stu-id="3526b-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="3526b-124">Obtém um ponteiro de interface para um objeto de ICorDebugValue que representa uma exceção que está sendo atualmente gerada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3526b-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="3526b-125">Método GetDebugState</span><span class="sxs-lookup"><span data-stu-id="3526b-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="3526b-126">Obtém um valor de CorDebugThreadState que descreve o estado atual de depuração deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-127">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="3526b-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="3526b-128">Obtém o identificador atual para a parte ativa disso `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-129">Método GetID</span><span class="sxs-lookup"><span data-stu-id="3526b-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="3526b-130">Obtém o identificador de sistema operacional atual da parte ativa disso `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-131">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="3526b-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="3526b-132">Obtém um ponteiro de interface para o thread comum a language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3526b-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="3526b-133">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="3526b-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="3526b-134">Obtém um ponteiro de interface para o processo do qual este `ICorDebugThread` faz parte.</span><span class="sxs-lookup"><span data-stu-id="3526b-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="3526b-135">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="3526b-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="3526b-136">Obtém um ponteiro de interface para o conjunto de registro associado a este `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-137">Método GetUserState</span><span class="sxs-lookup"><span data-stu-id="3526b-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="3526b-138">Obtém uma combinação bit a bit de valores de CorDebugUserState que descrevem o estado atual deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3526b-139">Método SetDebugState</span><span class="sxs-lookup"><span data-stu-id="3526b-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="3526b-140">Define uma combinação bit a bit de `CorDebugThreadState` valores que descrevem o estado de depuração deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3526b-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3526b-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="3526b-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3526b-142">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="3526b-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3526b-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3526b-143">Requirements</span></span>  
 <span data-ttu-id="3526b-144">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3526b-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3526b-145">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3526b-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3526b-146">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3526b-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3526b-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3526b-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3526b-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3526b-148">See also</span></span>
- [<span data-ttu-id="3526b-149">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3526b-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
