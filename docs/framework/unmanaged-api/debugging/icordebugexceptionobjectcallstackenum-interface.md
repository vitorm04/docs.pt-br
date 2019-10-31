---
title: Interface ICorDebugExceptionObjectCallStackEnum
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: 99a700270794ca92356cb9d134cb869d456199f9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084437"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="2eeea-102">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="2eeea-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="2eeea-103">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="2eeea-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="2eeea-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="2eeea-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2eeea-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2eeea-105">Methods</span></span>  
  
|<span data-ttu-id="2eeea-106">Método</span><span class="sxs-lookup"><span data-stu-id="2eeea-106">Method</span></span>|<span data-ttu-id="2eeea-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2eeea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2eeea-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="2eeea-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="2eeea-109">Obtém um número especificado de objetos [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) que contêm informações sobre uma pilha de chamadas do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="2eeea-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eeea-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2eeea-110">Remarks</span></span>  
 <span data-ttu-id="2eeea-111">A interface `ICorDebugExceptionObjectCallStackEnum` implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="2eeea-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="2eeea-112">Uma instância de `ICorDebugExceptionObjectCallStackEnum` é populada com objetos [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) chamando o método [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2eeea-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="2eeea-113">Os itens da pilha de chamadas na coleção podem ser enumerados chamando o método [ICorDebugExceptionObjectCallStackEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="2eeea-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eeea-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2eeea-114">Requirements</span></span>  
 <span data-ttu-id="2eeea-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eeea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eeea-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2eeea-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2eeea-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2eeea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eeea-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eeea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eeea-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2eeea-119">See also</span></span>

- [<span data-ttu-id="2eeea-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2eeea-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2eeea-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="2eeea-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
