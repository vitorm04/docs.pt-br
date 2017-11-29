---
title: "Método ICorDebugExceptionDebugEvent::GetStackPointer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17a7540c25eb1273add430c3a8ae01eea35497e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="8f8b9-102">Método ICorDebugExceptionDebugEvent::GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="8f8b9-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="8f8b9-103">Obtém o ponteiro de pilha para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f8b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f8b9-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f8b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f8b9-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="8f8b9-106">[out] Eventos de depuração de um ponteiro para o endereço do ponteiro de pilha para essa exceção.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="8f8b9-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f8b9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f8b9-108">Remarks</span></span>  
 <span data-ttu-id="8f8b9-109">O significado deste ponteiro de pilha depende do tipo de evento, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="8f8b9-110">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="8f8b9-110">Event type</span></span>|<span data-ttu-id="8f8b9-111">Significado da `pStackPointer` valor</span><span class="sxs-lookup"><span data-stu-id="8f8b9-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="8f8b9-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="8f8b9-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8f8b9-113">O ponteiro de pilha do quadro que lançou a exceção.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="8f8b9-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="8f8b9-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8f8b9-115">O ponteiro de pilha para o quadro de código do usuário mais próximo ao ponto da exceção lançada.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="8f8b9-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="8f8b9-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8f8b9-117">O ponteiro de pilha do quadro que contém o manipulador catch.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="8f8b9-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="8f8b9-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8f8b9-119">`pStackPointer` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8f8b9-120">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="8f8b9-121">O tipo de evento é proveniente do [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8f8b9-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f8b9-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f8b9-122">Requirements</span></span>  
 <span data-ttu-id="8f8b9-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f8b9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f8b9-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f8b9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f8b9-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f8b9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f8b9-126">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f8b9-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8b9-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f8b9-127">See Also</span></span>  
 [<span data-ttu-id="8f8b9-128">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="8f8b9-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="8f8b9-129">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="8f8b9-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
