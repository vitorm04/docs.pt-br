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
ms.openlocfilehash: 9d98bccdfb83cec547b185693c28f25017d3225f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782807"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="a70ca-102">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="a70ca-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="a70ca-103">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="a70ca-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="a70ca-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="a70ca-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a70ca-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a70ca-105">Methods</span></span>  
  
|<span data-ttu-id="a70ca-106">Método</span><span class="sxs-lookup"><span data-stu-id="a70ca-106">Method</span></span>|<span data-ttu-id="a70ca-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a70ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a70ca-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="a70ca-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="a70ca-109">Obtém um número especificado de objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) que contêm informações sobre uma pilha de chamadas do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="a70ca-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a70ca-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a70ca-110">Remarks</span></span>  
 <span data-ttu-id="a70ca-111">A interface `ICorDebugExceptionObjectCallStackEnum` implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="a70ca-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a70ca-112">Uma instância de `ICorDebugExceptionObjectCallStackEnum` é populada com objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) chamando o método [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a70ca-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="a70ca-113">Os itens da pilha de chamadas na coleção podem ser enumerados chamando o método [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="a70ca-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a70ca-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a70ca-114">Requirements</span></span>  
 <span data-ttu-id="a70ca-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a70ca-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70ca-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a70ca-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a70ca-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a70ca-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a70ca-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a70ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70ca-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="a70ca-119">See also</span></span>

- [<span data-ttu-id="a70ca-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a70ca-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a70ca-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="a70ca-121">Debugging</span></span>](index.md)
