---
title: Método ICorDebugBreakpointEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87249dae0eff4ea4899a63c0d13e79c266df453a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745012"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="a70a6-102">Método ICorDebugBreakpointEnum::Next</span><span class="sxs-lookup"><span data-stu-id="a70a6-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="a70a6-103">Obtém o número especificado de instâncias de ICorDebugBreakpoint de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="a70a6-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a70a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a70a6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a70a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a70a6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a70a6-106">[in] O número de `ICorDebugBreakpoint` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="a70a6-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="a70a6-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugBreakpoint` objeto que representa um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="a70a6-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a70a6-108">[out] Um ponteiro para o número de `ICorDebugBreakpoint` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="a70a6-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="a70a6-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="a70a6-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a70a6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a70a6-110">Requirements</span></span>  
 <span data-ttu-id="a70a6-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70a6-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a70a6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a70a6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a70a6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a70a6-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a70a6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
