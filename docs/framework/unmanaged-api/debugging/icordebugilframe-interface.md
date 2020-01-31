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
ms.openlocfilehash: 7a27b8ec512498c7bf817aca36267c37d8070a4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788577"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="6c68b-102">Interface ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="6c68b-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="6c68b-103">Representa um quadro de pilha do código MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="6c68b-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="6c68b-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="6c68b-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c68b-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6c68b-105">Methods</span></span>  
  
|<span data-ttu-id="6c68b-106">Método</span><span class="sxs-lookup"><span data-stu-id="6c68b-106">Method</span></span>|<span data-ttu-id="6c68b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c68b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c68b-108">Método CanSetIP</span><span class="sxs-lookup"><span data-stu-id="6c68b-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="6c68b-109">Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="6c68b-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="6c68b-110">Método EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="6c68b-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="6c68b-111">Obtém um enumerador para os argumentos neste quadro.</span><span class="sxs-lookup"><span data-stu-id="6c68b-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="6c68b-112">Método EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="6c68b-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="6c68b-113">Obtém um enumerador para as variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="6c68b-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="6c68b-114">Método GetArgument</span><span class="sxs-lookup"><span data-stu-id="6c68b-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="6c68b-115">Obtém o valor do argumento especificado neste quadro de pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="6c68b-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="6c68b-116">Método GetIP</span><span class="sxs-lookup"><span data-stu-id="6c68b-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="6c68b-117">Obtém o valor do ponteiro de instrução e um valor de combinação de bits que descreve como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="6c68b-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="6c68b-118">Método GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="6c68b-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="6c68b-119">Obtém o valor da variável local especificada neste quadro da pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="6c68b-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="6c68b-120">Método GetStackDepth</span><span class="sxs-lookup"><span data-stu-id="6c68b-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="6c68b-121">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="6c68b-121">Not implemented.</span></span>|  
|[<span data-ttu-id="6c68b-122">Método GetStackValue</span><span class="sxs-lookup"><span data-stu-id="6c68b-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="6c68b-123">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="6c68b-123">Not implemented.</span></span>|  
|[<span data-ttu-id="6c68b-124">Método SetIP</span><span class="sxs-lookup"><span data-stu-id="6c68b-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="6c68b-125">Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL.</span><span class="sxs-lookup"><span data-stu-id="6c68b-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c68b-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c68b-126">Remarks</span></span>  
 <span data-ttu-id="6c68b-127">A interface `ICorDebugILFrame` é uma interface ICorDebugFrame especializada.</span><span class="sxs-lookup"><span data-stu-id="6c68b-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="6c68b-128">Ele é usado para quadros de código MSIL ou para quadros compilados just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="6c68b-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="6c68b-129">Os quadros compilados em JIT implementam a interface de `ICorDebugILFrame` e a interface ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="6c68b-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c68b-130">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="6c68b-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c68b-131">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="6c68b-131">Requirements</span></span>  
 <span data-ttu-id="6c68b-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c68b-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c68b-133">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c68b-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c68b-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c68b-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c68b-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c68b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c68b-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="6c68b-136">See also</span></span>

- [<span data-ttu-id="6c68b-137">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6c68b-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
