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
ms.openlocfilehash: 1c60d7685de1e9a1d4f631ad1fba53b981829f58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159790"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="9750c-102">Interface ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="9750c-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="9750c-103">Representa um quadro de pilha do código Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="9750c-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="9750c-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="9750c-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9750c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9750c-105">Methods</span></span>  
  
|<span data-ttu-id="9750c-106">Método</span><span class="sxs-lookup"><span data-stu-id="9750c-106">Method</span></span>|<span data-ttu-id="9750c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9750c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9750c-108">Método CanSetIP</span><span class="sxs-lookup"><span data-stu-id="9750c-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="9750c-109">Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="9750c-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="9750c-110">Método EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="9750c-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="9750c-111">Obtém um enumerador para os argumentos neste quadro.</span><span class="sxs-lookup"><span data-stu-id="9750c-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="9750c-112">Método EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="9750c-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="9750c-113">Obtém um enumerador para as variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="9750c-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="9750c-114">Método GetArgument</span><span class="sxs-lookup"><span data-stu-id="9750c-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="9750c-115">Obtém o valor do argumento especificado neste quadro de pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="9750c-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="9750c-116">Método GetIP</span><span class="sxs-lookup"><span data-stu-id="9750c-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="9750c-117">Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="9750c-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="9750c-118">Método GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="9750c-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="9750c-119">Obtém o valor da variável local especificada neste quadro de pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="9750c-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="9750c-120">Método GetStackDepth</span><span class="sxs-lookup"><span data-stu-id="9750c-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="9750c-121">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="9750c-121">Not implemented.</span></span>|  
|[<span data-ttu-id="9750c-122">Método GetStackValue</span><span class="sxs-lookup"><span data-stu-id="9750c-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="9750c-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="9750c-123">Not implemented.</span></span>|  
|[<span data-ttu-id="9750c-124">Método SetIP</span><span class="sxs-lookup"><span data-stu-id="9750c-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="9750c-125">Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL.</span><span class="sxs-lookup"><span data-stu-id="9750c-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9750c-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="9750c-126">Remarks</span></span>  
 <span data-ttu-id="9750c-127">O `ICorDebugILFrame` é uma interface ICorDebugFrame especializada.</span><span class="sxs-lookup"><span data-stu-id="9750c-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="9750c-128">Ela é usada para quadros de código MSIL ou para just-in-time (JIT) compilados quadros.</span><span class="sxs-lookup"><span data-stu-id="9750c-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="9750c-129">Os quadros compilado por JIT implementam ambos o `ICorDebugILFrame` interface e a interface ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="9750c-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9750c-130">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="9750c-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9750c-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9750c-131">Requirements</span></span>  
 <span data-ttu-id="9750c-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9750c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9750c-133">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9750c-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9750c-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9750c-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9750c-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9750c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9750c-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9750c-136">See also</span></span>

- [<span data-ttu-id="9750c-137">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9750c-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
