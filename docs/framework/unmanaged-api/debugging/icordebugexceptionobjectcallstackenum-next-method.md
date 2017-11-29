---
title: "Método ICorDebugExceptionObjectCallStackEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum::Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a5d17bc46f6c2cab0d0d44f42e7b4741f67dbc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="f0418-102">Método ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f0418-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="f0418-103">Obtém o número especificado de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instâncias que contêm informações da pilha de chamadas de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="f0418-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0418-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0418-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0418-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0418-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f0418-106">[in] O número de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="f0418-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="f0418-107">[out] Uma matriz de ponteiros, cada qual apontando para um [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="f0418-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f0418-108">[out] Um ponteiro para o número de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="f0418-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0418-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0418-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0418-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0418-110">Requirements</span></span>  
 <span data-ttu-id="f0418-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0418-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0418-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0418-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0418-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0418-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0418-114">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0418-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0418-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0418-115">See Also</span></span>  
 [<span data-ttu-id="f0418-116">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="f0418-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 [<span data-ttu-id="f0418-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="f0418-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
