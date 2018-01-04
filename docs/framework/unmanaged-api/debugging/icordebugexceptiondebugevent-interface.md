---
title: Interface ICorDebugExceptionDebugEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97bbd9374b8a3f938f42b8ddd001049a2e7a324c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="f0799-102">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="f0799-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="f0799-103">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="f0799-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0799-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f0799-104">Methods</span></span>  
  
|<span data-ttu-id="f0799-105">Método</span><span class="sxs-lookup"><span data-stu-id="f0799-105">Method</span></span>|<span data-ttu-id="f0799-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0799-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0799-107">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="f0799-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="f0799-108">Obtém um sinalizador que indica se a exceção é pode ser interceptadas.</span><span class="sxs-lookup"><span data-stu-id="f0799-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="f0799-109">Método GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="f0799-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="f0799-110">Obtém o ponteiro de interface nativa para esse evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="f0799-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="f0799-111">Método GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="f0799-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="f0799-112">Obtém o ponteiro de pilha para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="f0799-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0799-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0799-113">Remarks</span></span>  
 <span data-ttu-id="f0799-114">O `ICorDebugExceptionDebugEvent` interface é implementada pelos seguintes tipos de evento:</span><span class="sxs-lookup"><span data-stu-id="f0799-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="f0799-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f0799-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="f0799-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f0799-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="f0799-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="f0799-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="f0799-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="f0799-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="f0799-119">A interface está disponível com o .NET Native somente.</span><span class="sxs-lookup"><span data-stu-id="f0799-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="f0799-120">Tentando chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0799-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0799-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0799-121">Requirements</span></span>  
 <span data-ttu-id="f0799-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0799-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0799-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0799-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0799-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0799-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0799-125">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0799-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0799-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0799-126">See Also</span></span>  
 [<span data-ttu-id="f0799-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f0799-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f0799-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="f0799-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
