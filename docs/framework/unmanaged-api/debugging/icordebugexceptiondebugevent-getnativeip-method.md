---
title: "Método ICorDebugExceptionDebugEvent::GetNativeIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32e75a18645c000562cdd94478c6ef8db41a01a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="2a05a-102">Método ICorDebugExceptionDebugEvent::GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="2a05a-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="2a05a-103">Obtém o ponteiro de instrução nativo para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="2a05a-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a05a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a05a-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a05a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a05a-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="2a05a-106">[out] Eventos de depuração de um ponteiro para o ponteiro de instrução para essa exceção.</span><span class="sxs-lookup"><span data-stu-id="2a05a-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="2a05a-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2a05a-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a05a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a05a-108">Remarks</span></span>  
 <span data-ttu-id="2a05a-109">O significado deste ponteiro de instrução depende do tipo de evento, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a05a-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="2a05a-110">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="2a05a-110">Event type</span></span>|<span data-ttu-id="2a05a-111">Significado da `pStackPointer` valor</span><span class="sxs-lookup"><span data-stu-id="2a05a-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="2a05a-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2a05a-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2a05a-113">O endereço da instrução com falha.</span><span class="sxs-lookup"><span data-stu-id="2a05a-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="2a05a-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2a05a-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2a05a-115">O endereço de código no quadro indicado pelo [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) método em que a execução será retomada se nenhuma exceção tivesse sido gerada.</span><span class="sxs-lookup"><span data-stu-id="2a05a-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="2a05a-116">A exceção podem ou não pode causar um código diferente, como o bloco catch de uma `try/catch/finally` cláusula, para ser executado nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="2a05a-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="2a05a-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="2a05a-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2a05a-118">O código de endereço onde `catch` será iniciar a execução do manipulador no quadro indicado pelo [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2a05a-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="2a05a-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="2a05a-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2a05a-120">`pIP` é 0.</span><span class="sxs-lookup"><span data-stu-id="2a05a-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="2a05a-121">O tipo de evento é proveniente do [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2a05a-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a05a-122">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2a05a-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a05a-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a05a-123">Requirements</span></span>  
 <span data-ttu-id="2a05a-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a05a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a05a-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a05a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a05a-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a05a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a05a-127">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a05a-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a05a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a05a-128">See Also</span></span>  
 [<span data-ttu-id="2a05a-129">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="2a05a-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="2a05a-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2a05a-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
