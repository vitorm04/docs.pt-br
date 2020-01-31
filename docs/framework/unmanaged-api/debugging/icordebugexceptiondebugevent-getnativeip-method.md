---
title: 'Método ICorDebugExceptionDebugEvent:: GetNativeIP'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788680"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="deae6-102">Método ICorDebugExceptionDebugEvent:: GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="deae6-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="deae6-103">Obtém o ponteiro de instrução nativa para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="deae6-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deae6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="deae6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deae6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="deae6-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="deae6-106">fora Um ponteiro para o ponteiro de instrução deste evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="deae6-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="deae6-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="deae6-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="deae6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="deae6-108">Remarks</span></span>  
 <span data-ttu-id="deae6-109">O significado desse ponteiro de instrução depende do tipo de evento, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="deae6-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="deae6-110">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="deae6-110">Event type</span></span>|<span data-ttu-id="deae6-111">Significado do valor de `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="deae6-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="deae6-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="deae6-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="deae6-113">O endereço da instrução com falha.</span><span class="sxs-lookup"><span data-stu-id="deae6-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="deae6-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="deae6-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="deae6-115">O endereço do código no quadro indicado pelo método [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) em que a execução será retomada se nenhuma exceção tivesse sido gerada.</span><span class="sxs-lookup"><span data-stu-id="deae6-115">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="deae6-116">A exceção pode ou não causar código diferente, como o bloco catch de uma cláusula `try/catch/finally`, a ser executada nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="deae6-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="deae6-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="deae6-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="deae6-118">O endereço de código em que `catch` execução do manipulador será iniciada no quadro indicado pelo método [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="deae6-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="deae6-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="deae6-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="deae6-120">`pIP` é 0.</span><span class="sxs-lookup"><span data-stu-id="deae6-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="deae6-121">O tipo de evento está disponível no método [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="deae6-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="deae6-122">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="deae6-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deae6-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="deae6-123">Requirements</span></span>  
 <span data-ttu-id="deae6-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deae6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deae6-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="deae6-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deae6-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="deae6-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deae6-127">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deae6-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deae6-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="deae6-128">See also</span></span>

- [<span data-ttu-id="deae6-129">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="deae6-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="deae6-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="deae6-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
