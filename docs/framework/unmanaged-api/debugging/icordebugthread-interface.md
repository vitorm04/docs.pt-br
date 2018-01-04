---
title: ICorDebugThread Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread
helpviewer_keywords: ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2df43a35e510695d7af0c38cbb8fb3b051f5f354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread-interface1"></a><span data-ttu-id="5973c-102">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="5973c-102">ICorDebugThread Interface1</span></span>
<span data-ttu-id="5973c-103">Representa um thread em um processo.</span><span class="sxs-lookup"><span data-stu-id="5973c-103">Represents a thread in a process.</span></span> <span data-ttu-id="5973c-104">O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.</span><span class="sxs-lookup"><span data-stu-id="5973c-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5973c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5973c-105">Methods</span></span>  
  
|<span data-ttu-id="5973c-106">Método</span><span class="sxs-lookup"><span data-stu-id="5973c-106">Method</span></span>|<span data-ttu-id="5973c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5973c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5973c-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="5973c-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="5973c-109">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="5973c-109">This method is not implemented.</span></span> <span data-ttu-id="5973c-110">Não o use.</span><span class="sxs-lookup"><span data-stu-id="5973c-110">Do not use it.</span></span>|  
|[<span data-ttu-id="5973c-111">Método CreateEval</span><span class="sxs-lookup"><span data-stu-id="5973c-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="5973c-112">Cria um objeto de ICorDebugEval que opera sobre isso `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-113">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="5973c-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="5973c-114">Cria um objeto de ICorDebugStepper que permite percorrer o quadro ativo na `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-115">Método EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="5973c-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="5973c-116">Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-117">Método GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="5973c-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="5973c-118">Obtém um ponteiro de interface para o ativo ICorDebugChain neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-119">Método GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="5973c-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="5973c-120">Obtém um ponteiro de interface para o ativo ICorDebugFrame neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-121">Método GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="5973c-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="5973c-122">Obtém um ponteiro de interface para o domínio de aplicativo no qual este `ICorDebugThread` está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="5973c-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="5973c-123">Método GetCurrentException</span><span class="sxs-lookup"><span data-stu-id="5973c-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="5973c-124">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa uma exceção atualmente sendo lançada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5973c-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="5973c-125">Método GetDebugState</span><span class="sxs-lookup"><span data-stu-id="5973c-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="5973c-126">Obtém um valor de CorDebugThreadState que descreve o estado atual de depuração deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-127">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="5973c-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="5973c-128">Obtém o identificador atual para a parte ativa disso `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-129">Método GetID</span><span class="sxs-lookup"><span data-stu-id="5973c-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="5973c-130">Obtém o identificador de sistema operacional atual da parte ativa disso `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-131">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="5973c-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="5973c-132">Obtém um ponteiro de interface para o thread de runtime (CLR) de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="5973c-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="5973c-133">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="5973c-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="5973c-134">Obtém um ponteiro de interface para o processo do qual este `ICorDebugThread` faz parte.</span><span class="sxs-lookup"><span data-stu-id="5973c-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="5973c-135">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="5973c-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="5973c-136">Obtém um ponteiro de interface para o conjunto de registro associado a esta `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-137">Método GetUserState</span><span class="sxs-lookup"><span data-stu-id="5973c-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="5973c-138">Obtém uma combinação bit a bit dos valores de CorDebugUserState que descrevem o estado atual deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5973c-139">Método SetDebugState</span><span class="sxs-lookup"><span data-stu-id="5973c-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="5973c-140">Define uma combinação bit a bit de `CorDebugThreadState` valores que descrevem o estado de depuração deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5973c-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5973c-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="5973c-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5973c-142">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="5973c-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5973c-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5973c-143">Requirements</span></span>  
 <span data-ttu-id="5973c-144">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5973c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5973c-145">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5973c-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5973c-146">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5973c-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5973c-147">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5973c-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5973c-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5973c-148">See Also</span></span>  
 [<span data-ttu-id="5973c-149">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5973c-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
