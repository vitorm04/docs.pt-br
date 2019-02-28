---
title: Interface ICorDebugILFrame
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a10c39d7df12c86b8fcf0fb40389c087f96e1ee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965963"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="fc182-102">Interface ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="fc182-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="fc182-103">Representa um quadro de pilha do código Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="fc182-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="fc182-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="fc182-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc182-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="fc182-105">Methods</span></span>  
  
|<span data-ttu-id="fc182-106">Método</span><span class="sxs-lookup"><span data-stu-id="fc182-106">Method</span></span>|<span data-ttu-id="fc182-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc182-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc182-108">Método CanSetIP</span><span class="sxs-lookup"><span data-stu-id="fc182-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="fc182-109">Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="fc182-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="fc182-110">Método EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="fc182-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="fc182-111">Obtém um enumerador para os argumentos neste quadro.</span><span class="sxs-lookup"><span data-stu-id="fc182-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="fc182-112">Método EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="fc182-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="fc182-113">Obtém um enumerador para as variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="fc182-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="fc182-114">Método GetArgument</span><span class="sxs-lookup"><span data-stu-id="fc182-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="fc182-115">Obtém o valor do argumento especificado neste quadro de pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="fc182-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="fc182-116">Método GetIP</span><span class="sxs-lookup"><span data-stu-id="fc182-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="fc182-117">Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="fc182-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="fc182-118">Método GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="fc182-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="fc182-119">Obtém o valor da variável local especificada neste quadro de pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="fc182-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="fc182-120">Método GetStackDepth</span><span class="sxs-lookup"><span data-stu-id="fc182-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="fc182-121">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="fc182-121">Not implemented.</span></span>|  
|[<span data-ttu-id="fc182-122">Método GetStackValue</span><span class="sxs-lookup"><span data-stu-id="fc182-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="fc182-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="fc182-123">Not implemented.</span></span>|  
|[<span data-ttu-id="fc182-124">Método SetIP</span><span class="sxs-lookup"><span data-stu-id="fc182-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="fc182-125">Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL.</span><span class="sxs-lookup"><span data-stu-id="fc182-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc182-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc182-126">Remarks</span></span>  
 <span data-ttu-id="fc182-127">O `ICorDebugILFrame` é uma interface ICorDebugFrame especializada.</span><span class="sxs-lookup"><span data-stu-id="fc182-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="fc182-128">Ela é usada para quadros de código MSIL ou para just-in-time (JIT) compilados quadros.</span><span class="sxs-lookup"><span data-stu-id="fc182-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="fc182-129">Os quadros compilado por JIT implementam ambos o `ICorDebugILFrame` interface e a interface ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="fc182-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc182-130">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="fc182-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc182-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc182-131">Requirements</span></span>  
 <span data-ttu-id="fc182-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc182-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc182-133">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc182-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc182-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc182-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc182-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc182-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc182-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc182-136">See also</span></span>
- [<span data-ttu-id="fc182-137">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fc182-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
