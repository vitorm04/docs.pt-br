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
ms.openlocfilehash: f4bacfe94178ea78b1c3afd15a2e100076c38a84
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777989"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="42859-102">Interface ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="42859-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="42859-103">Representa um segmento de uma pilha de chamadas física ou lógica.</span><span class="sxs-lookup"><span data-stu-id="42859-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42859-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="42859-104">Methods</span></span>  
  
|<span data-ttu-id="42859-105">Método</span><span class="sxs-lookup"><span data-stu-id="42859-105">Method</span></span>|<span data-ttu-id="42859-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="42859-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42859-107">Método EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="42859-107">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="42859-108">Obtém um enumerador que contém todos os quadros de pilha gerenciados na cadeia, começando com o quadro mais recente.</span><span class="sxs-lookup"><span data-stu-id="42859-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="42859-109">Método GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="42859-109">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="42859-110">Obtém o quadro ativo (ou seja, mais recente) na cadeia.</span><span class="sxs-lookup"><span data-stu-id="42859-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="42859-111">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="42859-111">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="42859-112">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="42859-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="42859-113">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="42859-113">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="42859-114">Obtém a cadeia que chamou essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="42859-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="42859-115">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="42859-115">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="42859-116">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="42859-116">Not implemented.</span></span>|  
|[<span data-ttu-id="42859-117">Método GetNext</span><span class="sxs-lookup"><span data-stu-id="42859-117">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="42859-118">Obtém a próxima cadeia de quadros para o thread.</span><span class="sxs-lookup"><span data-stu-id="42859-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="42859-119">Método GetPrevious</span><span class="sxs-lookup"><span data-stu-id="42859-119">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="42859-120">Obtém a cadeia de quadros anterior para o thread.</span><span class="sxs-lookup"><span data-stu-id="42859-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="42859-121">Método GetReason</span><span class="sxs-lookup"><span data-stu-id="42859-121">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="42859-122">Obtém o motivo do Genesis desta cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="42859-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="42859-123">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="42859-123">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="42859-124">Obtém o conjunto de registros para a parte ativa desta cadeia.</span><span class="sxs-lookup"><span data-stu-id="42859-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="42859-125">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="42859-125">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="42859-126">Obtém o intervalo de endereços do segmento da pilha para esta cadeia.</span><span class="sxs-lookup"><span data-stu-id="42859-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="42859-127">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="42859-127">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="42859-128">Obtém o thread físico para o qual esta cadeia de chamadas faz parte.</span><span class="sxs-lookup"><span data-stu-id="42859-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="42859-129">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="42859-129">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="42859-130">Obtém um valor que indica se esta cadeia está executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="42859-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42859-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="42859-131">Remarks</span></span>  
 <span data-ttu-id="42859-132">Os quadros de pilha em uma cadeia ocupam um espaço de pilha contíguo e compartilham o mesmo thread e contexto.</span><span class="sxs-lookup"><span data-stu-id="42859-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="42859-133">Uma cadeia pode representar cadeias de código gerenciados ou não-gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="42859-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="42859-134">Uma instância de `ICorDebugChain` vazia representa uma cadeia de código não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="42859-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42859-135">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="42859-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42859-136">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="42859-136">Requirements</span></span>  
 <span data-ttu-id="42859-137">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42859-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42859-138">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42859-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42859-139">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42859-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42859-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42859-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42859-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="42859-141">See also</span></span>

- [<span data-ttu-id="42859-142">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="42859-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
