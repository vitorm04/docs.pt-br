---
title: Método ICorDebugExceptionDebugEvent::GetStackPointer
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9d4c0a1938edd3e2fe88ea6e418b3430f1b5cb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163196"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="9d1d3-102">Método ICorDebugExceptionDebugEvent::GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="9d1d3-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="9d1d3-103">Obtém o ponteiro de pilha para esse evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d1d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d1d3-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d1d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d1d3-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="9d1d3-106">[out] Evento de depuração de um ponteiro para o endereço do ponteiro de pilha para essa exceção.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="9d1d3-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d1d3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d1d3-108">Remarks</span></span>  
 <span data-ttu-id="9d1d3-109">O significado deste ponteiro de pilha depende do tipo de evento, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="9d1d3-110">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="9d1d3-110">Event type</span></span>|<span data-ttu-id="9d1d3-111">Significado do `pStackPointer` valor</span><span class="sxs-lookup"><span data-stu-id="9d1d3-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="9d1d3-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="9d1d3-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="9d1d3-113">O ponteiro de pilha para o quadro que gerou a exceção.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="9d1d3-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="9d1d3-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="9d1d3-115">O ponteiro de pilha para o quadro de código do usuário mais próximo ao ponto da exceção lançada.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="9d1d3-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="9d1d3-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="9d1d3-117">O ponteiro de pilha para o quadro que contém o manipulador catch.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="9d1d3-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="9d1d3-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="9d1d3-119">`pStackPointer` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9d1d3-120">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="9d1d3-121">O tipo de evento é proveniente de [icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="9d1d3-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d1d3-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d1d3-122">Requirements</span></span>  
 <span data-ttu-id="9d1d3-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d1d3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d1d3-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d1d3-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d1d3-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d1d3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d1d3-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d1d3-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d1d3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d1d3-127">See also</span></span>

- [<span data-ttu-id="9d1d3-128">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="9d1d3-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="9d1d3-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9d1d3-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
