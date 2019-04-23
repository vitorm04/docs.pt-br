---
title: Método ICorDebugExceptionDebugEvent::GetNativeIP
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2455e52e46edd7fc8d4d6e8b003d3ebfd87ea07f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085825"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="0964b-102">Método ICorDebugExceptionDebugEvent::GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="0964b-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="0964b-103">Obtém o ponteiro de instrução nativo para esse evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="0964b-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0964b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0964b-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0964b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0964b-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="0964b-106">[out] Evento de depuração de um ponteiro para o ponteiro de instrução para essa exceção.</span><span class="sxs-lookup"><span data-stu-id="0964b-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="0964b-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0964b-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0964b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0964b-108">Remarks</span></span>  
 <span data-ttu-id="0964b-109">O significado de neste ponteiro de instrução depende do tipo de evento, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="0964b-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="0964b-110">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="0964b-110">Event type</span></span>|<span data-ttu-id="0964b-111">Significado do `pStackPointer` valor</span><span class="sxs-lookup"><span data-stu-id="0964b-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="0964b-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0964b-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0964b-113">O endereço da instrução de falha.</span><span class="sxs-lookup"><span data-stu-id="0964b-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="0964b-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0964b-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0964b-115">O endereço de código no quadro indicado pelo [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) método em que a execução será retomada se nenhuma exceção tivesse sido gerada.</span><span class="sxs-lookup"><span data-stu-id="0964b-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="0964b-116">A exceção pode causar ou não código diferente, como o bloco catch de uma `try/catch/finally` cláusula, a ser executada neste quadro.</span><span class="sxs-lookup"><span data-stu-id="0964b-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="0964b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="0964b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0964b-118">O código de endereço onde `catch` execução do manipulador será iniciada no quadro indicado pela [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0964b-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="0964b-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="0964b-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0964b-120">`pIP` é 0.</span><span class="sxs-lookup"><span data-stu-id="0964b-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="0964b-121">O tipo de evento é proveniente de [icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0964b-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0964b-122">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0964b-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0964b-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0964b-123">Requirements</span></span>  
 <span data-ttu-id="0964b-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0964b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0964b-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0964b-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0964b-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0964b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0964b-127">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0964b-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0964b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0964b-128">See also</span></span>

- [<span data-ttu-id="0964b-129">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="0964b-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="0964b-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0964b-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
