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
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124068"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="acbc9-102">Interface ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="acbc9-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="acbc9-103">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="acbc9-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acbc9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="acbc9-104">Methods</span></span>  
  
|<span data-ttu-id="acbc9-105">Método</span><span class="sxs-lookup"><span data-stu-id="acbc9-105">Method</span></span>|<span data-ttu-id="acbc9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="acbc9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acbc9-107">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="acbc9-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="acbc9-108">Obtém um ICorDebugStepper para executar operações de depuração relativas a esse `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="acbc9-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="acbc9-109">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="acbc9-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="acbc9-110">Obtém um ponteiro para a `ICorDebugFrame` na cadeia atual que esse quadro chamou ou retorna NULL se esse for o quadro interno na cadeia.</span><span class="sxs-lookup"><span data-stu-id="acbc9-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="acbc9-111">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="acbc9-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="acbc9-112">Obtém um ponteiro para a `ICorDebugFrame` na cadeia atual que chamou esse quadro ou retorna NULL se esse for o quadro mais externo na cadeia.</span><span class="sxs-lookup"><span data-stu-id="acbc9-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="acbc9-113">Método GetChain</span><span class="sxs-lookup"><span data-stu-id="acbc9-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="acbc9-114">Obtém um ponteiro para o ICorDebugChain para o qual este `ICorDebugFrame` faz parte.</span><span class="sxs-lookup"><span data-stu-id="acbc9-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="acbc9-115">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="acbc9-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="acbc9-116">Obtém um ponteiro para o ICorDebugCode associado a este quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="acbc9-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="acbc9-117">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="acbc9-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="acbc9-118">Obtém um ponteiro para o ICorDebugFunction que contém o código associado a esse quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="acbc9-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="acbc9-119">Método GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="acbc9-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="acbc9-120">Obtém o token de metadados para a função que contém o código associado a esse quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="acbc9-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="acbc9-121">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="acbc9-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="acbc9-122">Obtém o intervalo de endereços absolutos do registro de ativação representado por este `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="acbc9-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acbc9-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="acbc9-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acbc9-124">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="acbc9-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acbc9-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="acbc9-125">Requirements</span></span>  
 <span data-ttu-id="acbc9-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acbc9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acbc9-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acbc9-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acbc9-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acbc9-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acbc9-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acbc9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acbc9-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acbc9-130">See also</span></span>

- [<span data-ttu-id="acbc9-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="acbc9-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
