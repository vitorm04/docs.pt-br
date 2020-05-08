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
ms.openlocfilehash: af90886390b59932d3ae146a70fc2901ec1c378d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894666"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="397ff-102">Método ICorDebugBreakpointEnum::Next</span><span class="sxs-lookup"><span data-stu-id="397ff-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="397ff-103">Obtém o número especificado de instâncias de ICorDebugBreakpoint da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="397ff-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="397ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="397ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="397ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="397ff-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="397ff-106">no O número de `ICorDebugBreakpoint` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="397ff-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="397ff-107">fora Uma matriz de ponteiros, cada um dos quais aponta `ICorDebugBreakpoint` para um objeto que representa um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="397ff-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="397ff-108">fora Um ponteiro para o número de `ICorDebugBreakpoint` instâncias retornadas de fato.</span><span class="sxs-lookup"><span data-stu-id="397ff-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="397ff-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="397ff-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="397ff-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="397ff-110">Requirements</span></span>  
 <span data-ttu-id="397ff-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="397ff-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="397ff-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="397ff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="397ff-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="397ff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="397ff-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="397ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
