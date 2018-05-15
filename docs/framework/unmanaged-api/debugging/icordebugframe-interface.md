---
title: ICorDebugFrame Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3d6c1a2bfd66e275b506d4465731c48cd7c6515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="56171-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="56171-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="56171-103">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="56171-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56171-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="56171-104">Methods</span></span>  
  
|<span data-ttu-id="56171-105">Método</span><span class="sxs-lookup"><span data-stu-id="56171-105">Method</span></span>|<span data-ttu-id="56171-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="56171-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56171-107">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="56171-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="56171-108">Obtém um ICorDebugStepper para executar operações de revisão em relação a esse `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="56171-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="56171-109">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="56171-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="56171-110">Obtém um ponteiro para o `ICorDebugFrame` da cadeia atual que este quadro chamado ou retorna null se esse é o quadro interno na cadeia.</span><span class="sxs-lookup"><span data-stu-id="56171-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="56171-111">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="56171-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="56171-112">Obtém um ponteiro para o `ICorDebugFrame` da atual cadeia que chamadas a este quadro ou retorna null se esse é o quadro externo da cadeia.</span><span class="sxs-lookup"><span data-stu-id="56171-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="56171-113">Método GetChain</span><span class="sxs-lookup"><span data-stu-id="56171-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="56171-114">Obtém um ponteiro para o ICorDebugChain isso `ICorDebugFrame` faz parte.</span><span class="sxs-lookup"><span data-stu-id="56171-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="56171-115">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="56171-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="56171-116">Obtém um ponteiro para o ICorDebugCode associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="56171-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="56171-117">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="56171-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="56171-118">Obtém um ponteiro para o ICorDebugFunction que contém o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="56171-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="56171-119">Método GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="56171-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="56171-120">Obtém o token de metadados para a função que contém o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="56171-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="56171-121">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="56171-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="56171-122">Obtém o intervalo de endereço absoluto do quadro de pilhas representado por esse `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="56171-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56171-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="56171-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56171-124">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="56171-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56171-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56171-125">Requirements</span></span>  
 <span data-ttu-id="56171-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56171-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56171-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56171-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56171-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56171-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56171-129">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56171-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56171-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56171-130">See Also</span></span>  
 [<span data-ttu-id="56171-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="56171-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
