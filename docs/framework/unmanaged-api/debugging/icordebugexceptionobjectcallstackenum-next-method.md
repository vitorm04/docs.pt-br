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
ms.openlocfilehash: 6fce9f61e222d0fc1763495de162a94a7fc22689
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975973"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="2d03b-102">Método ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="2d03b-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="2d03b-103">Obtém o número especificado de instâncias [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) que contêm informações de uma pilha de chamadas do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="2d03b-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d03b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d03b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d03b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d03b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2d03b-106">no O número de instâncias de [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="2d03b-106">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="2d03b-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="2d03b-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2d03b-108">fora Um ponteiro para o número de instâncias de [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) retornadas na verdade.</span><span class="sxs-lookup"><span data-stu-id="2d03b-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d03b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d03b-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d03b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d03b-110">Requirements</span></span>  
 <span data-ttu-id="2d03b-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d03b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d03b-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d03b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d03b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d03b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d03b-114">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d03b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d03b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d03b-115">See also</span></span>

- [<span data-ttu-id="2d03b-116">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="2d03b-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="2d03b-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2d03b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
