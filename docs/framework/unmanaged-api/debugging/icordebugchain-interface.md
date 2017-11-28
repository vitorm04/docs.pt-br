---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain
helpviewer_keywords: ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f964b5390e601b518acad44dd6fd170399ff0af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="6e7f6-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="6e7f6-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="6e7f6-103">Representa um segmento de uma pilha de chamadas física ou lógica.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e7f6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6e7f6-104">Methods</span></span>  
  
|<span data-ttu-id="6e7f6-105">Método</span><span class="sxs-lookup"><span data-stu-id="6e7f6-105">Method</span></span>|<span data-ttu-id="6e7f6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e7f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e7f6-107">Método EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="6e7f6-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="6e7f6-108">Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="6e7f6-109">Método GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="6e7f6-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="6e7f6-110">Obtém o ativo (ou seja, mais recente) quadro da cadeia.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="6e7f6-111">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="6e7f6-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="6e7f6-112">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="6e7f6-113">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="6e7f6-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="6e7f6-114">Obtém a cadeia que chamou essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="6e7f6-115">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="6e7f6-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="6e7f6-116">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-116">Not implemented.</span></span>|  
|[<span data-ttu-id="6e7f6-117">Método GetNext</span><span class="sxs-lookup"><span data-stu-id="6e7f6-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="6e7f6-118">Obtém a próxima cadeia de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="6e7f6-119">Método GetPrevious</span><span class="sxs-lookup"><span data-stu-id="6e7f6-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="6e7f6-120">Obtém a cadeia anterior de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="6e7f6-121">Método GetReason</span><span class="sxs-lookup"><span data-stu-id="6e7f6-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="6e7f6-122">Obtém o motivo para genesis dessa cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="6e7f6-123">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="6e7f6-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="6e7f6-124">Obtém o conjunto de registros de parte ativa dessa cadeia.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="6e7f6-125">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="6e7f6-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="6e7f6-126">Obtém o intervalo de endereços do segmento de pilha para essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="6e7f6-127">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="6e7f6-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="6e7f6-128">Obtém o segmento físico que essa cadeia de chamada é parte do.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="6e7f6-129">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="6e7f6-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="6e7f6-130">Obtém um valor que indica se esta cadeia está em execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e7f6-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e7f6-131">Remarks</span></span>  
 <span data-ttu-id="6e7f6-132">Os quadros de pilha em uma cadeia ocupam espaço de pilha contíguas e compartilham o mesmo thread e o contexto.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="6e7f6-133">Uma cadeia pode representar ou cadeias de código gerenciado ou não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="6e7f6-134">Vazio `ICorDebugChain` instância representa uma cadeia de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e7f6-135">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="6e7f6-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e7f6-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e7f6-136">Requirements</span></span>  
 <span data-ttu-id="6e7f6-137">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e7f6-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e7f6-138">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e7f6-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e7f6-139">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e7f6-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e7f6-140">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e7f6-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7f6-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e7f6-141">See Also</span></span>  
 [<span data-ttu-id="6e7f6-142">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="6e7f6-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
