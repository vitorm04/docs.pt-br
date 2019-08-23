---
title: Interface ICorDebugChain
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93ada40bd88e53cd06f5e8d8136b2d527d7741e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969299"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="0c8f0-102">Interface ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="0c8f0-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="0c8f0-103">Representa um segmento de uma pilha de chamadas física ou lógica.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c8f0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0c8f0-104">Methods</span></span>  
  
|<span data-ttu-id="0c8f0-105">Método</span><span class="sxs-lookup"><span data-stu-id="0c8f0-105">Method</span></span>|<span data-ttu-id="0c8f0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c8f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c8f0-107">Método EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="0c8f0-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="0c8f0-108">Obtém um enumerador que contém todos os quadros de pilha gerenciados na cadeia, começando com o quadro mais recente.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="0c8f0-109">Método GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="0c8f0-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="0c8f0-110">Obtém o quadro ativo (ou seja, mais recente) na cadeia.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="0c8f0-111">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="0c8f0-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="0c8f0-112">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="0c8f0-113">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="0c8f0-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="0c8f0-114">Obtém a cadeia que chamou essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="0c8f0-115">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="0c8f0-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="0c8f0-116">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-116">Not implemented.</span></span>|  
|[<span data-ttu-id="0c8f0-117">Método GetNext</span><span class="sxs-lookup"><span data-stu-id="0c8f0-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="0c8f0-118">Obtém a próxima cadeia de quadros para o thread.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="0c8f0-119">Método GetPrevious</span><span class="sxs-lookup"><span data-stu-id="0c8f0-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="0c8f0-120">Obtém a cadeia de quadros anterior para o thread.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="0c8f0-121">Método GetReason</span><span class="sxs-lookup"><span data-stu-id="0c8f0-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="0c8f0-122">Obtém o motivo do Genesis desta cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="0c8f0-123">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="0c8f0-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="0c8f0-124">Obtém o conjunto de registros para a parte ativa desta cadeia.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="0c8f0-125">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="0c8f0-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="0c8f0-126">Obtém o intervalo de endereços do segmento da pilha para esta cadeia.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="0c8f0-127">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="0c8f0-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="0c8f0-128">Obtém o thread físico para o qual esta cadeia de chamadas faz parte.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="0c8f0-129">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="0c8f0-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="0c8f0-130">Obtém um valor que indica se esta cadeia está executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c8f0-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c8f0-131">Remarks</span></span>  
 <span data-ttu-id="0c8f0-132">Os quadros de pilha em uma cadeia ocupam um espaço de pilha contíguo e compartilham o mesmo thread e contexto.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="0c8f0-133">Uma cadeia pode representar cadeias de código gerenciados ou não-gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="0c8f0-134">Uma instância `ICorDebugChain` vazia representa uma cadeia de código não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c8f0-135">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="0c8f0-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8f0-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c8f0-136">Requirements</span></span>  
 <span data-ttu-id="0c8f0-137">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8f0-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8f0-138">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c8f0-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c8f0-139">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c8f0-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c8f0-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8f0-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8f0-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c8f0-141">See also</span></span>

- [<span data-ttu-id="0c8f0-142">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0c8f0-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
