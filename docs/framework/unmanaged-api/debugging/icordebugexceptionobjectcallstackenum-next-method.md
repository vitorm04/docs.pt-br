---
title: Método ICorDebugExceptionObjectCallStackEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 998256d75e5a0efd368ff7eb60d0023c8db0e283
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531048"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="b88c6-102">Método ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="b88c6-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="b88c6-103">Obtém o número especificado de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instâncias que contêm informações da pilha de chamadas de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="b88c6-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b88c6-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b88c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b88c6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b88c6-106">[in] O número de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="b88c6-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="b88c6-107">[out] Uma matriz de ponteiros, cada qual apontando para um [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="b88c6-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b88c6-108">[out] Um ponteiro para o número de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="b88c6-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b88c6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b88c6-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b88c6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b88c6-110">Requirements</span></span>  
 <span data-ttu-id="b88c6-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b88c6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b88c6-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b88c6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b88c6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b88c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b88c6-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b88c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88c6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b88c6-115">See also</span></span>
- [<span data-ttu-id="b88c6-116">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="b88c6-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="b88c6-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b88c6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
