---
title: Interface ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: dfa65aa1b63c996068e75ff1165111d5fcfe77eb
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975999"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="00477-102">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="00477-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="00477-103">Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para dar suporte a eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="00477-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00477-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="00477-104">Methods</span></span>  
  
|<span data-ttu-id="00477-105">Método</span><span class="sxs-lookup"><span data-stu-id="00477-105">Method</span></span>|<span data-ttu-id="00477-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="00477-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00477-107">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="00477-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="00477-108">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="00477-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="00477-109">Método GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="00477-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="00477-110">Obtém o ponteiro de interface nativa para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="00477-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="00477-111">Método GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="00477-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="00477-112">Obtém o ponteiro de pilha para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="00477-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00477-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="00477-113">Remarks</span></span>  
 <span data-ttu-id="00477-114">A `ICorDebugExceptionDebugEvent` interface é implementada pelos seguintes tipos de evento:</span><span class="sxs-lookup"><span data-stu-id="00477-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="00477-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="00477-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="00477-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="00477-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="00477-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="00477-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="00477-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="00477-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="00477-119">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="00477-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="00477-120">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface `E_NOINTERFACE` retorna para cenários ICorDebug fora do .net Native.</span><span class="sxs-lookup"><span data-stu-id="00477-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00477-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00477-121">Requirements</span></span>  
 <span data-ttu-id="00477-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00477-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00477-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00477-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00477-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00477-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00477-125">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00477-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00477-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00477-126">See also</span></span>

- [<span data-ttu-id="00477-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="00477-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="00477-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="00477-128">Debugging</span></span>](index.md)
