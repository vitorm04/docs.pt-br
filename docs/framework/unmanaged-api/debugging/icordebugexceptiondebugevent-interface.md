---
title: Interface ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 522bccb4a424da620063995d02ae15d09ecbf2fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929872"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="5941f-102">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="5941f-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="5941f-103">Estende a interface [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) para dar suporte a eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="5941f-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5941f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5941f-104">Methods</span></span>  
  
|<span data-ttu-id="5941f-105">Método</span><span class="sxs-lookup"><span data-stu-id="5941f-105">Method</span></span>|<span data-ttu-id="5941f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5941f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5941f-107">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="5941f-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="5941f-108">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="5941f-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="5941f-109">Método GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="5941f-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="5941f-110">Obtém o ponteiro de interface nativa para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="5941f-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="5941f-111">Método GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="5941f-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="5941f-112">Obtém o ponteiro de pilha para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="5941f-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5941f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="5941f-113">Remarks</span></span>  
 <span data-ttu-id="5941f-114">A `ICorDebugExceptionDebugEvent` interface é implementada pelos seguintes tipos de evento:</span><span class="sxs-lookup"><span data-stu-id="5941f-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="5941f-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="5941f-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="5941f-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="5941f-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="5941f-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="5941f-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="5941f-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="5941f-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="5941f-119">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5941f-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="5941f-120">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface `E_NOINTERFACE` retorna para cenários ICorDebug fora do .net Native.</span><span class="sxs-lookup"><span data-stu-id="5941f-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5941f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5941f-121">Requirements</span></span>  
 <span data-ttu-id="5941f-122">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5941f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5941f-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5941f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5941f-124">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5941f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5941f-125">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5941f-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5941f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5941f-126">See also</span></span>

- [<span data-ttu-id="5941f-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5941f-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5941f-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="5941f-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
