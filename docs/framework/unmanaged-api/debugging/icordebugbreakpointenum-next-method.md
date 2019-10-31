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
ms.openlocfilehash: d29576c6f073f1d0e8e0aea417fc38c09a8327c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122741"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="b43d1-102">Método ICorDebugBreakpointEnum::Next</span><span class="sxs-lookup"><span data-stu-id="b43d1-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="b43d1-103">Obtém o número especificado de instâncias de ICorDebugBreakpoint da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="b43d1-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b43d1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b43d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b43d1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b43d1-106">no O número de instâncias de `ICorDebugBreakpoint` a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="b43d1-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="b43d1-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto `ICorDebugBreakpoint` que representa um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="b43d1-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b43d1-108">fora Um ponteiro para o número de instâncias de `ICorDebugBreakpoint` retornadas na verdade.</span><span class="sxs-lookup"><span data-stu-id="b43d1-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="b43d1-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="b43d1-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43d1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b43d1-110">Requirements</span></span>  
 <span data-ttu-id="b43d1-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b43d1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43d1-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b43d1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b43d1-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b43d1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b43d1-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43d1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
