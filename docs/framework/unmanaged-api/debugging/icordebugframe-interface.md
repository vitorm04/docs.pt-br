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
ms.openlocfilehash: ba138e79e0d6fb6f9c5e9c3efe3466f3c88cccae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782619"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="5ee84-102">Interface ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="5ee84-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="5ee84-103">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="5ee84-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ee84-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5ee84-104">Methods</span></span>  
  
|<span data-ttu-id="5ee84-105">Método</span><span class="sxs-lookup"><span data-stu-id="5ee84-105">Method</span></span>|<span data-ttu-id="5ee84-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ee84-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ee84-107">Método CreateStepper</span><span class="sxs-lookup"><span data-stu-id="5ee84-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="5ee84-108">Obtém um ICorDebugStepper para executar operações de depuração relativas a esse `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="5ee84-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="5ee84-109">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="5ee84-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="5ee84-110">Obtém um ponteiro para a `ICorDebugFrame` na cadeia atual que esse quadro chamou ou retorna NULL se esse for o quadro interno na cadeia.</span><span class="sxs-lookup"><span data-stu-id="5ee84-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="5ee84-111">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="5ee84-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="5ee84-112">Obtém um ponteiro para a `ICorDebugFrame` na cadeia atual que chamou esse quadro ou retorna NULL se esse for o quadro mais externo na cadeia.</span><span class="sxs-lookup"><span data-stu-id="5ee84-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="5ee84-113">Método GetChain</span><span class="sxs-lookup"><span data-stu-id="5ee84-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="5ee84-114">Obtém um ponteiro para o ICorDebugChain para o qual este `ICorDebugFrame` faz parte.</span><span class="sxs-lookup"><span data-stu-id="5ee84-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="5ee84-115">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="5ee84-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="5ee84-116">Obtém um ponteiro para o ICorDebugCode associado a este quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="5ee84-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="5ee84-117">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="5ee84-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="5ee84-118">Obtém um ponteiro para o ICorDebugFunction que contém o código associado a esse quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="5ee84-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="5ee84-119">Método GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="5ee84-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="5ee84-120">Obtém o token de metadados para a função que contém o código associado a esse quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="5ee84-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="5ee84-121">Método GetStackRange</span><span class="sxs-lookup"><span data-stu-id="5ee84-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="5ee84-122">Obtém o intervalo de endereços absolutos do registro de ativação representado por este `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="5ee84-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ee84-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ee84-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ee84-124">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="5ee84-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee84-125">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5ee84-125">Requirements</span></span>  
 <span data-ttu-id="5ee84-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ee84-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ee84-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ee84-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ee84-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ee84-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ee84-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee84-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee84-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="5ee84-130">See also</span></span>

- [<span data-ttu-id="5ee84-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5ee84-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
