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
ms.openlocfilehash: b227b374021136e78f7f061d235eb18eca5b9515
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791483"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="21948-102">Interface ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="21948-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="21948-103">Representa um thread em um processo.</span><span class="sxs-lookup"><span data-stu-id="21948-103">Represents a thread in a process.</span></span> <span data-ttu-id="21948-104">O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.</span><span class="sxs-lookup"><span data-stu-id="21948-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21948-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="21948-105">Methods</span></span>  
  
|<span data-ttu-id="21948-106">Método</span><span class="sxs-lookup"><span data-stu-id="21948-106">Method</span></span>|<span data-ttu-id="21948-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="21948-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21948-108">Método ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="21948-108">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="21948-109">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="21948-109">This method is not implemented.</span></span> <span data-ttu-id="21948-110">Não o use.</span><span class="sxs-lookup"><span data-stu-id="21948-110">Do not use it.</span></span>|  
|[<span data-ttu-id="21948-111">Método CreateEval</span><span class="sxs-lookup"><span data-stu-id="21948-111">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="21948-112">Cria um objeto ICorDebugEval que opera neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-113">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="21948-113">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="21948-114">Cria um objeto ICorDebugStepper que permite percorrer o quadro ativo neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-115">Método EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="21948-115">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="21948-116">Obtém um ponteiro de interface para um enumerador ICorDebugChainEnum que contém todas as cadeias de pilha nesta `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-117">Método GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="21948-117">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="21948-118">Obtém um ponteiro de interface para o ICorDebugChain ativo neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-119">Método GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="21948-119">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="21948-120">Obtém um ponteiro de interface para o ICorDebugFrame ativo neste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-121">Método GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="21948-121">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="21948-122">Obtém um ponteiro de interface para o domínio do aplicativo no qual este `ICorDebugThread` está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="21948-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="21948-123">Método GetCurrentException</span><span class="sxs-lookup"><span data-stu-id="21948-123">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="21948-124">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa uma exceção que está sendo lançada atualmente pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="21948-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="21948-125">Método GetDebugState</span><span class="sxs-lookup"><span data-stu-id="21948-125">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="21948-126">Obtém um valor de CorDebugThreadState que descreve o estado de depuração atual desta `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-127">Método GetHandle</span><span class="sxs-lookup"><span data-stu-id="21948-127">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="21948-128">Obtém o identificador atual da parte ativa deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-129">Método GetID</span><span class="sxs-lookup"><span data-stu-id="21948-129">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="21948-130">Obtém o identificador do sistema operacional atual da parte ativa deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-131">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="21948-131">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="21948-132">Obtém um ponteiro de interface para o thread Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="21948-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="21948-133">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="21948-133">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="21948-134">Obtém um ponteiro de interface para o processo do qual esse `ICorDebugThread` forma uma parte.</span><span class="sxs-lookup"><span data-stu-id="21948-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="21948-135">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="21948-135">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="21948-136">Obtém um ponteiro de interface para o conjunto de registros associado a este `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-137">Método GetUserState</span><span class="sxs-lookup"><span data-stu-id="21948-137">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="21948-138">Obtém uma combinação de bits de valor CorDebugUserState que descreve o estado atual desta `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="21948-139">Método SetDebugState</span><span class="sxs-lookup"><span data-stu-id="21948-139">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="21948-140">Define uma combinação de bits de `CorDebugThreadState` de valores que descreve o estado de depuração deste `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="21948-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21948-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="21948-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21948-142">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="21948-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21948-143">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="21948-143">Requirements</span></span>  
 <span data-ttu-id="21948-144">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21948-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21948-145">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21948-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21948-146">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21948-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21948-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21948-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21948-148">Veja também</span><span class="sxs-lookup"><span data-stu-id="21948-148">See also</span></span>

- [<span data-ttu-id="21948-149">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="21948-149">Debugging Interfaces</span></span>](debugging-interfaces.md)
