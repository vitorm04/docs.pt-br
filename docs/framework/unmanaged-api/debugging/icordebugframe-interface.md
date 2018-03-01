---
title: ICorDebugFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: caa3ef9cd52cc872d4ebc96376c104a7b90fb4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="2c4a3-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="2c4a3-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="2c4a3-103">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c4a3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2c4a3-104">Methods</span></span>  
  
|<span data-ttu-id="2c4a3-105">Método</span><span class="sxs-lookup"><span data-stu-id="2c4a3-105">Method</span></span>|<span data-ttu-id="2c4a3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c4a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c4a3-107">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="2c4a3-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="2c4a3-108">Obtém um ICorDebugStepper para executar operações de revisão em relação a esse `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="2c4a3-109">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="2c4a3-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="2c4a3-110">Obtém um ponteiro para o `ICorDebugFrame` da cadeia atual que este quadro chamado ou retorna null se esse é o quadro interno na cadeia.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2c4a3-111">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="2c4a3-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="2c4a3-112">Obtém um ponteiro para o `ICorDebugFrame` da atual cadeia que chamadas a este quadro ou retorna null se esse é o quadro externo da cadeia.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2c4a3-113">Método GetChain</span><span class="sxs-lookup"><span data-stu-id="2c4a3-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="2c4a3-114">Obtém um ponteiro para o ICorDebugChain isso `ICorDebugFrame` faz parte.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="2c4a3-115">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="2c4a3-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="2c4a3-116">Obtém um ponteiro para o ICorDebugCode associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2c4a3-117">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="2c4a3-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="2c4a3-118">Obtém um ponteiro para o ICorDebugFunction que contém o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2c4a3-119">Método GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="2c4a3-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="2c4a3-120">Obtém o token de metadados para a função que contém o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2c4a3-121">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="2c4a3-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="2c4a3-122">Obtém o intervalo de endereço absoluto do quadro de pilhas representado por esse `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c4a3-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c4a3-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c4a3-124">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="2c4a3-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c4a3-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c4a3-125">Requirements</span></span>  
 <span data-ttu-id="2c4a3-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c4a3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c4a3-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c4a3-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c4a3-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c4a3-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c4a3-129">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c4a3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4a3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c4a3-130">See Also</span></span>  
 [<span data-ttu-id="2c4a3-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2c4a3-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
