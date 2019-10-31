---
title: Método ICorDebugValueEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: 09394acb07b8595f99d9ecc873eb0985cdd79316
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134590"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="3e541-102">Método ICorDebugValueEnum::Next</span><span class="sxs-lookup"><span data-stu-id="3e541-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="3e541-103">Obtém o número especificado de instâncias "ICorDebugValue" da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="3e541-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e541-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e541-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e541-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e541-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3e541-106">no O número de instâncias de `ICorDebugValue` a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="3e541-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3e541-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="3e541-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3e541-108">fora Aponta para o número de instâncias de `ICorDebugValue` retornadas na verdade.</span><span class="sxs-lookup"><span data-stu-id="3e541-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="3e541-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="3e541-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e541-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e541-110">Requirements</span></span>  
 <span data-ttu-id="3e541-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e541-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e541-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e541-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e541-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e541-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e541-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e541-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e541-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e541-115">See also</span></span>
