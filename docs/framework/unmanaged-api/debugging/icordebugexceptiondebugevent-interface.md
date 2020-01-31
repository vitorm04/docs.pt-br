---
title: Interface ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: 168ba2945608a5b26432c5a0f583e5d406f6ce9b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782823"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="c97e9-102">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="c97e9-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="c97e9-103">Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para dar suporte a eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="c97e9-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c97e9-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c97e9-104">Methods</span></span>  
  
|<span data-ttu-id="c97e9-105">Método</span><span class="sxs-lookup"><span data-stu-id="c97e9-105">Method</span></span>|<span data-ttu-id="c97e9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c97e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c97e9-107">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="c97e9-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="c97e9-108">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="c97e9-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="c97e9-109">Método GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="c97e9-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="c97e9-110">Obtém o ponteiro de interface nativa para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="c97e9-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="c97e9-111">Método GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="c97e9-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="c97e9-112">Obtém o ponteiro de pilha para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="c97e9-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c97e9-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c97e9-113">Remarks</span></span>  
 <span data-ttu-id="c97e9-114">A interface `ICorDebugExceptionDebugEvent` é implementada pelos seguintes tipos de evento:</span><span class="sxs-lookup"><span data-stu-id="c97e9-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="c97e9-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c97e9-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="c97e9-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c97e9-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="c97e9-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="c97e9-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="c97e9-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="c97e9-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="c97e9-119">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c97e9-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="c97e9-120">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c97e9-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c97e9-121">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c97e9-121">Requirements</span></span>  
 <span data-ttu-id="c97e9-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c97e9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97e9-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c97e9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c97e9-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c97e9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c97e9-125">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c97e9-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97e9-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="c97e9-126">See also</span></span>

- [<span data-ttu-id="c97e9-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c97e9-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c97e9-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="c97e9-128">Debugging</span></span>](index.md)
