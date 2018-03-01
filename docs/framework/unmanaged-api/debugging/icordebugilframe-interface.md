---
title: ICorDebugILFrame Interface1
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="61414-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="61414-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="61414-103">Representa um quadro de pilha do código Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="61414-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="61414-104">Esta interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="61414-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61414-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="61414-105">Methods</span></span>  
  
|<span data-ttu-id="61414-106">Método</span><span class="sxs-lookup"><span data-stu-id="61414-106">Method</span></span>|<span data-ttu-id="61414-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="61414-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61414-108">Método CanSetIP</span><span class="sxs-lookup"><span data-stu-id="61414-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="61414-109">Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="61414-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="61414-110">Método EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="61414-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="61414-111">Obtém um enumerador para os argumentos nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="61414-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="61414-112">Método EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="61414-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="61414-113">Obtém um enumerador para as variáveis locais nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="61414-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="61414-114">Método GetArgument</span><span class="sxs-lookup"><span data-stu-id="61414-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="61414-115">Obtém o valor do argumento especificado nesse quadro de pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="61414-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="61414-116">Método GetIP</span><span class="sxs-lookup"><span data-stu-id="61414-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="61414-117">Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="61414-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="61414-118">Método GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="61414-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="61414-119">Obtém o valor da variável local especificada deste quadro de pilhas MSIL.</span><span class="sxs-lookup"><span data-stu-id="61414-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="61414-120">Método GetStackDepth</span><span class="sxs-lookup"><span data-stu-id="61414-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="61414-121">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="61414-121">Not implemented.</span></span>|  
|[<span data-ttu-id="61414-122">Método GetStackValue</span><span class="sxs-lookup"><span data-stu-id="61414-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="61414-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="61414-123">Not implemented.</span></span>|  
|[<span data-ttu-id="61414-124">Método SetIP</span><span class="sxs-lookup"><span data-stu-id="61414-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="61414-125">Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL.</span><span class="sxs-lookup"><span data-stu-id="61414-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61414-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="61414-126">Remarks</span></span>  
 <span data-ttu-id="61414-127">O `ICorDebugILFrame` é uma interface ICorDebugFrame especializada.</span><span class="sxs-lookup"><span data-stu-id="61414-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="61414-128">Ele é usado para os quadros de código MSIL ou just-in-time (JIT) compilados quadros.</span><span class="sxs-lookup"><span data-stu-id="61414-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="61414-129">Os quadros de compilação JIT implementam o `ICorDebugILFrame` interface e a interface ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="61414-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61414-130">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="61414-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61414-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61414-131">Requirements</span></span>  
 <span data-ttu-id="61414-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61414-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61414-133">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61414-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61414-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61414-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61414-135">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61414-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61414-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61414-136">See Also</span></span>  
 [<span data-ttu-id="61414-137">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="61414-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
