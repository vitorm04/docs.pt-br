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
ms.openlocfilehash: 01dded47fca26df11781153eb45693057a25ad01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989372"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="0961c-102">Interface ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="0961c-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="0961c-103">Representa um segmento de uma pilha de chamadas física ou lógica.</span><span class="sxs-lookup"><span data-stu-id="0961c-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0961c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0961c-104">Methods</span></span>  
  
|<span data-ttu-id="0961c-105">Método</span><span class="sxs-lookup"><span data-stu-id="0961c-105">Method</span></span>|<span data-ttu-id="0961c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0961c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0961c-107">Método EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="0961c-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="0961c-108">Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.</span><span class="sxs-lookup"><span data-stu-id="0961c-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="0961c-109">Método GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="0961c-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="0961c-110">Obtém o ativo (ou seja, mais recente) quadro da cadeia.</span><span class="sxs-lookup"><span data-stu-id="0961c-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="0961c-111">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="0961c-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="0961c-112">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="0961c-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="0961c-113">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="0961c-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="0961c-114">Obtém a cadeia que chamou esta cadeia.</span><span class="sxs-lookup"><span data-stu-id="0961c-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="0961c-115">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="0961c-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="0961c-116">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="0961c-116">Not implemented.</span></span>|  
|[<span data-ttu-id="0961c-117">Método GetNext</span><span class="sxs-lookup"><span data-stu-id="0961c-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="0961c-118">Obtém a próxima cadeia de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="0961c-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="0961c-119">Método GetPrevious</span><span class="sxs-lookup"><span data-stu-id="0961c-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="0961c-120">Obtém a cadeia anterior de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="0961c-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="0961c-121">Método GetReason</span><span class="sxs-lookup"><span data-stu-id="0961c-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="0961c-122">Obtém o motivo para a gênese dessa cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="0961c-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="0961c-123">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="0961c-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="0961c-124">Obtém o conjunto de registros de parte ativa dessa cadeia.</span><span class="sxs-lookup"><span data-stu-id="0961c-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="0961c-125">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="0961c-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="0961c-126">Obtém o intervalo de endereços do segmento de pilha para essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="0961c-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="0961c-127">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="0961c-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="0961c-128">Obtém o thread físico que essa cadeia de chamada é parte do.</span><span class="sxs-lookup"><span data-stu-id="0961c-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="0961c-129">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="0961c-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="0961c-130">Obtém um valor que indica se esta cadeia está em execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0961c-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0961c-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="0961c-131">Remarks</span></span>  
 <span data-ttu-id="0961c-132">Os quadros de pilha em uma cadeia ocupam espaço na pilha contíguos e compartilham o mesmo thread e contexto.</span><span class="sxs-lookup"><span data-stu-id="0961c-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="0961c-133">Uma cadeia pode representar qualquer cadeias de código gerenciado ou não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0961c-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="0961c-134">Vazio `ICorDebugChain` instância representa uma cadeia de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0961c-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0961c-135">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="0961c-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0961c-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0961c-136">Requirements</span></span>  
 <span data-ttu-id="0961c-137">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0961c-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0961c-138">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0961c-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0961c-139">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0961c-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0961c-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0961c-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0961c-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0961c-141">See also</span></span>

- [<span data-ttu-id="0961c-142">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0961c-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
