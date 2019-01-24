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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00b52f9f058853ba14fcfd1986366527de25a427
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680696"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="029a4-102">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="029a4-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="029a4-103">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="029a4-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="029a4-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="029a4-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="029a4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="029a4-105">Methods</span></span>  
  
|<span data-ttu-id="029a4-106">Método</span><span class="sxs-lookup"><span data-stu-id="029a4-106">Method</span></span>|<span data-ttu-id="029a4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="029a4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="029a4-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="029a4-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="029a4-109">Obtém um número especificado de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objetos que contêm informações sobre a pilha de chamadas de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="029a4-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="029a4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="029a4-110">Remarks</span></span>  
 <span data-ttu-id="029a4-111">O `ICorDebugExceptionObjectCallStackEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="029a4-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="029a4-112">Uma `ICorDebugExceptionObjectCallStackEnum` instância é preenchida com [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objetos, chamando o [icordebugexceptionobjectvalue:: Enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="029a4-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="029a4-113">Os itens da pilha de chamada na coleção podem ser enumerados chamando o [icordebugexceptionobjectcallstackenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) método</span><span class="sxs-lookup"><span data-stu-id="029a4-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="029a4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="029a4-114">Requirements</span></span>  
 <span data-ttu-id="029a4-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="029a4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="029a4-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="029a4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="029a4-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="029a4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="029a4-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="029a4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029a4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="029a4-119">See also</span></span>
- [<span data-ttu-id="029a4-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="029a4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="029a4-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="029a4-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
