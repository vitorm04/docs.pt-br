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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161259"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="25f70-102">Interface ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="25f70-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="25f70-103">Uma implementação especializada de ICorDebugFrame usada para quadros nativos.</span><span class="sxs-lookup"><span data-stu-id="25f70-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25f70-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="25f70-104">Methods</span></span>  
  
|<span data-ttu-id="25f70-105">Método</span><span class="sxs-lookup"><span data-stu-id="25f70-105">Method</span></span>|<span data-ttu-id="25f70-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="25f70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25f70-107">Método CanSetIP</span><span class="sxs-lookup"><span data-stu-id="25f70-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="25f70-108">Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="25f70-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="25f70-109">Método GetIP</span><span class="sxs-lookup"><span data-stu-id="25f70-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="25f70-110">Obtém o deslocamento do quadro de pilha em código nativo.</span><span class="sxs-lookup"><span data-stu-id="25f70-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="25f70-111">Método GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="25f70-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="25f70-112">Obtém um ponteiro para um ICorDebugValue que representa o valor de um argumento ou variável local armazenado em dois registros de memória de um quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="25f70-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="25f70-113">Método GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="25f70-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="25f70-114">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, dos quais os bits baixos são armazenados no registro especificado e os bits altos são armazenados no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="25f70-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="25f70-115">Método GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="25f70-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="25f70-116">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local armazenado no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="25f70-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="25f70-117">Método GetLocalRegisterMemoryValue</span><span class="sxs-lookup"><span data-stu-id="25f70-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="25f70-118">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, dos quais os bits altos são armazenados no registro especificado e os bits baixos são armazenados no endereço de memória especificado</span><span class="sxs-lookup"><span data-stu-id="25f70-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="25f70-119">Método GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="25f70-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="25f70-120">Obtém um ponteiro para um `ICorDebugValue` que representa o valor de um argumento ou uma variável local armazenado no registro nativo especificado.</span><span class="sxs-lookup"><span data-stu-id="25f70-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="25f70-121">Método GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="25f70-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="25f70-122">Obtém um ponteiro para um [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) que representa o conjunto de registros de isso `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="25f70-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="25f70-123">Método SetIP</span><span class="sxs-lookup"><span data-stu-id="25f70-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="25f70-124">Define o ponteiro de instrução para o local de deslocamento especificado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="25f70-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25f70-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="25f70-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25f70-126">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="25f70-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f70-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25f70-127">Requirements</span></span>  
 <span data-ttu-id="25f70-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f70-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f70-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25f70-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25f70-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25f70-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25f70-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f70-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f70-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25f70-132">See also</span></span>

- [<span data-ttu-id="25f70-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="25f70-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
