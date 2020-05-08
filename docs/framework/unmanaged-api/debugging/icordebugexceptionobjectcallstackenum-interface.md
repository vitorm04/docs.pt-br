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
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975986"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="39e84-102">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="39e84-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="39e84-103">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="39e84-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="39e84-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="39e84-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39e84-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="39e84-105">Methods</span></span>  
  
|<span data-ttu-id="39e84-106">Método</span><span class="sxs-lookup"><span data-stu-id="39e84-106">Method</span></span>|<span data-ttu-id="39e84-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="39e84-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39e84-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="39e84-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="39e84-109">Obtém um número especificado de objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) que contêm informações sobre uma pilha de chamadas do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="39e84-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39e84-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="39e84-110">Remarks</span></span>  
 <span data-ttu-id="39e84-111">A `ICorDebugExceptionObjectCallStackEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="39e84-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="39e84-112">Uma `ICorDebugExceptionObjectCallStackEnum` instância é populada com objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) chamando o método [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="39e84-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="39e84-113">Os itens da pilha de chamadas na coleção podem ser enumerados chamando o método [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="39e84-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39e84-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39e84-114">Requirements</span></span>  
 <span data-ttu-id="39e84-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39e84-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39e84-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39e84-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39e84-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39e84-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39e84-118">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39e84-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e84-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39e84-119">See also</span></span>

- [<span data-ttu-id="39e84-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="39e84-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="39e84-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="39e84-121">Debugging</span></span>](index.md)
