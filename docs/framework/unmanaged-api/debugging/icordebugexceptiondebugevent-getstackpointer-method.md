---
title: 'Método ICorDebugExceptionDebugEvent:: GetStackPointer'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 688f5aec457298a43d95a35fdbc6e04e29a306a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084684"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="c8b7a-102">Método ICorDebugExceptionDebugEvent:: GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="c8b7a-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="c8b7a-103">Obtém o ponteiro de pilha para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b7a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8b7a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8b7a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8b7a-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="c8b7a-106">fora Um ponteiro para o endereço do ponteiro de pilha para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="c8b7a-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8b7a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8b7a-108">Remarks</span></span>  
 <span data-ttu-id="c8b7a-109">O significado desse ponteiro de pilha depende do tipo de evento, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c8b7a-110">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="c8b7a-110">Event type</span></span>|<span data-ttu-id="c8b7a-111">Significado do valor de `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="c8b7a-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="c8b7a-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c8b7a-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c8b7a-113">O ponteiro de pilha para o quadro que gerou a exceção.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="c8b7a-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c8b7a-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c8b7a-115">O ponteiro de pilha para o quadro de código do usuário mais próximo do ponto da exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="c8b7a-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="c8b7a-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c8b7a-117">O ponteiro de pilha para o quadro que contém o manipulador catch.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="c8b7a-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="c8b7a-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c8b7a-119">`pStackPointer` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c8b7a-120">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c8b7a-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="c8b7a-121">O tipo de evento está disponível no método [ICorDebugDebugEvent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c8b7a-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b7a-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8b7a-122">Requirements</span></span>  
 <span data-ttu-id="c8b7a-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8b7a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b7a-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8b7a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8b7a-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8b7a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8b7a-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b7a-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b7a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8b7a-127">See also</span></span>

- [<span data-ttu-id="c8b7a-128">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="c8b7a-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="c8b7a-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c8b7a-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
