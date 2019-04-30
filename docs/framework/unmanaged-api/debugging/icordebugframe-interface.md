---
title: Interface ICorDebugFrame
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
ms.openlocfilehash: a15d7f16676b8b9d66f8d1ba7484f3fec5735a44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988748"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="2f9aa-102">Interface ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="2f9aa-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="2f9aa-103">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f9aa-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2f9aa-104">Methods</span></span>  
  
|<span data-ttu-id="2f9aa-105">Método</span><span class="sxs-lookup"><span data-stu-id="2f9aa-105">Method</span></span>|<span data-ttu-id="2f9aa-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f9aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f9aa-107">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="2f9aa-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="2f9aa-108">Obtém um ICorDebugStepper para executar operações de passo a passo em relação a esse `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="2f9aa-109">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="2f9aa-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="2f9aa-110">Obtém um ponteiro para o `ICorDebugFrame` da cadeia atual que esse quadro chamado ou retorna nulo se esse é o quadro mais interno da cadeia.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2f9aa-111">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="2f9aa-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="2f9aa-112">Obtém um ponteiro para o `ICorDebugFrame` da atual cadeia que chamado este quadro ou retorna nulo se esse é o quadro mais externo na cadeia.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2f9aa-113">Método GetChain</span><span class="sxs-lookup"><span data-stu-id="2f9aa-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="2f9aa-114">Obtém um ponteiro para o ICorDebugChain essa `ICorDebugFrame` faz parte.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="2f9aa-115">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="2f9aa-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="2f9aa-116">Obtém um ponteiro para o ICorDebugCode associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2f9aa-117">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="2f9aa-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="2f9aa-118">Obtém um ponteiro para o ICorDebugFunction que contém o código associado a esse registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2f9aa-119">Método GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="2f9aa-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="2f9aa-120">Obtém o token de metadados para a função que contém o código associado a esse registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2f9aa-121">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="2f9aa-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="2f9aa-122">Obtém o intervalo de endereços absoluto do quadro de pilha representado por este `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f9aa-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f9aa-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f9aa-124">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f9aa-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f9aa-125">Requirements</span></span>  
 <span data-ttu-id="2f9aa-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f9aa-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f9aa-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f9aa-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f9aa-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f9aa-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f9aa-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f9aa-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9aa-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f9aa-130">See also</span></span>

- [<span data-ttu-id="2f9aa-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2f9aa-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
