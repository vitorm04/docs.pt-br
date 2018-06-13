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
ms.openlocfilehash: e6df9c7e24e2303571b7cb3b80ff4bf07dc59ccc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415659"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="26074-102">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="26074-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="26074-103">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="26074-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="26074-104">Esta interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="26074-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26074-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="26074-105">Methods</span></span>  
  
|<span data-ttu-id="26074-106">Método</span><span class="sxs-lookup"><span data-stu-id="26074-106">Method</span></span>|<span data-ttu-id="26074-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="26074-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26074-108">Icordebugexceptionobjectcallstackenum</span><span class="sxs-lookup"><span data-stu-id="26074-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="26074-109">Obtém um número especificado de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objetos que contêm informações sobre a pilha de chamadas de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="26074-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26074-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="26074-110">Remarks</span></span>  
 <span data-ttu-id="26074-111">O `ICorDebugExceptionObjectCallStackEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="26074-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="26074-112">Um `ICorDebugExceptionObjectCallStackEnum` instância é populada com [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objetos chamando o [Icordebugexceptionobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="26074-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="26074-113">Os itens da pilha de chamada na coleção podem ser enumerados chamando o [Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) método</span><span class="sxs-lookup"><span data-stu-id="26074-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26074-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26074-114">Requirements</span></span>  
 <span data-ttu-id="26074-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26074-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26074-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26074-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26074-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26074-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26074-118">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26074-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26074-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26074-119">See Also</span></span>  
 [<span data-ttu-id="26074-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="26074-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="26074-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="26074-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
