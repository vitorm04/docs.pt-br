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
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937002"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="8e51a-102">Interface ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="8e51a-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="8e51a-103">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="8e51a-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e51a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8e51a-104">Methods</span></span>  
  
|<span data-ttu-id="8e51a-105">Método</span><span class="sxs-lookup"><span data-stu-id="8e51a-105">Method</span></span>|<span data-ttu-id="8e51a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e51a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e51a-107">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="8e51a-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="8e51a-108">Obtém um ICorDebugStepper para executar operações de depuração relativas a `ICorDebugFrame`isso.</span><span class="sxs-lookup"><span data-stu-id="8e51a-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="8e51a-109">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="8e51a-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="8e51a-110">Obtém um ponteiro para o `ICorDebugFrame` na cadeia atual que este quadro chamou ou retorna NULL se esse for o quadro interno na cadeia.</span><span class="sxs-lookup"><span data-stu-id="8e51a-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="8e51a-111">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="8e51a-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="8e51a-112">Obtém um ponteiro para o `ICorDebugFrame` na cadeia atual que chamou esse quadro ou retorna NULL se esse for o quadro mais externo na cadeia.</span><span class="sxs-lookup"><span data-stu-id="8e51a-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="8e51a-113">Método GetChain</span><span class="sxs-lookup"><span data-stu-id="8e51a-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="8e51a-114">Obtém um ponteiro para o ICorDebugChain `ICorDebugFrame` que faz parte de.</span><span class="sxs-lookup"><span data-stu-id="8e51a-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="8e51a-115">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="8e51a-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="8e51a-116">Obtém um ponteiro para o ICorDebugCode associado a este quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="8e51a-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="8e51a-117">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="8e51a-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="8e51a-118">Obtém um ponteiro para o ICorDebugFunction que contém o código associado a esse quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="8e51a-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="8e51a-119">Método GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="8e51a-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="8e51a-120">Obtém o token de metadados para a função que contém o código associado a esse quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="8e51a-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="8e51a-121">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="8e51a-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="8e51a-122">Obtém o intervalo de endereços absolutos do quadro de pilha representado `ICorDebugFrame`por isso.</span><span class="sxs-lookup"><span data-stu-id="8e51a-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e51a-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e51a-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e51a-124">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="8e51a-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e51a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e51a-125">Requirements</span></span>  
 <span data-ttu-id="8e51a-126">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e51a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e51a-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e51a-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e51a-128">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e51a-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e51a-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e51a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e51a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e51a-130">See also</span></span>

- [<span data-ttu-id="8e51a-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8e51a-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
