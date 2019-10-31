---
title: Interface ICorDebugNativeFrame
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 04bdbc49217236bc6c05a718cb4d42067cafd8bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096670"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="40a36-102">Interface ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="40a36-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="40a36-103">Uma implementação especializada de ICorDebugFrame usada para quadros nativos.</span><span class="sxs-lookup"><span data-stu-id="40a36-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40a36-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="40a36-104">Methods</span></span>  
  
|<span data-ttu-id="40a36-105">Método</span><span class="sxs-lookup"><span data-stu-id="40a36-105">Method</span></span>|<span data-ttu-id="40a36-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="40a36-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40a36-107">Método CanSetIP</span><span class="sxs-lookup"><span data-stu-id="40a36-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="40a36-108">Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="40a36-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="40a36-109">Método GetIP</span><span class="sxs-lookup"><span data-stu-id="40a36-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="40a36-110">Obtém o deslocamento do quadro de pilha no código nativo.</span><span class="sxs-lookup"><span data-stu-id="40a36-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="40a36-111">Método GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="40a36-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="40a36-112">Obtém um ponteiro para um ICorDebugValue que representa o valor de um argumento ou variável local armazenado em dois registros de memória de um quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="40a36-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="40a36-113">Método GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="40a36-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="40a36-114">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, da qual os bits baixos são armazenados no registro especificado e os bits altos são armazenados no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="40a36-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="40a36-115">Método GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="40a36-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="40a36-116">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local armazenada no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="40a36-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="40a36-117">Método GetLocalRegisterMemoryValue</span><span class="sxs-lookup"><span data-stu-id="40a36-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="40a36-118">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, da qual os bits altos são armazenados no registro especificado e os bits baixos são armazenados no endereço de memória especificado</span><span class="sxs-lookup"><span data-stu-id="40a36-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="40a36-119">Método GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="40a36-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="40a36-120">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de um argumento ou uma variável local armazenada no registro nativo especificado.</span><span class="sxs-lookup"><span data-stu-id="40a36-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="40a36-121">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="40a36-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="40a36-122">Obtém um ponteiro para um [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) que representa o conjunto de registros para este `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="40a36-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="40a36-123">Método SetIP</span><span class="sxs-lookup"><span data-stu-id="40a36-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="40a36-124">Define o ponteiro de instrução para o local de deslocamento especificado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="40a36-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40a36-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="40a36-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40a36-126">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="40a36-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40a36-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40a36-127">Requirements</span></span>  
 <span data-ttu-id="40a36-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40a36-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40a36-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40a36-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40a36-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40a36-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40a36-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40a36-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a36-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40a36-132">See also</span></span>

- [<span data-ttu-id="40a36-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="40a36-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
