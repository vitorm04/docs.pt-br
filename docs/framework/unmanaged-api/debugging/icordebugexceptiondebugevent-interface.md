---
title: Interface ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d8af540bc6c4e14931ccadc49c7285e7caa7862
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651176"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="db5e4-102">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="db5e4-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="db5e4-103">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="db5e4-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db5e4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="db5e4-104">Methods</span></span>  
  
|<span data-ttu-id="db5e4-105">Método</span><span class="sxs-lookup"><span data-stu-id="db5e4-105">Method</span></span>|<span data-ttu-id="db5e4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="db5e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db5e4-107">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="db5e4-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="db5e4-108">Obtém um sinalizador que indica se a exceção é que pode ser interceptadas.</span><span class="sxs-lookup"><span data-stu-id="db5e4-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="db5e4-109">Método GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="db5e4-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="db5e4-110">Obtém o ponteiro de interface nativa para esse evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="db5e4-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="db5e4-111">Método GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="db5e4-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="db5e4-112">Obtém o ponteiro de pilha para esse evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="db5e4-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db5e4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="db5e4-113">Remarks</span></span>  
 <span data-ttu-id="db5e4-114">O `ICorDebugExceptionDebugEvent` interface é implementada pelos seguintes tipos de evento:</span><span class="sxs-lookup"><span data-stu-id="db5e4-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="db5e4-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="db5e4-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="db5e4-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="db5e4-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="db5e4-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="db5e4-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="db5e4-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="db5e4-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="db5e4-119">A interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="db5e4-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="db5e4-120">A tentativa de chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="db5e4-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db5e4-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db5e4-121">Requirements</span></span>  
 <span data-ttu-id="db5e4-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db5e4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db5e4-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db5e4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db5e4-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db5e4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db5e4-125">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db5e4-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5e4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db5e4-126">See also</span></span>

- [<span data-ttu-id="db5e4-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="db5e4-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="db5e4-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="db5e4-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
