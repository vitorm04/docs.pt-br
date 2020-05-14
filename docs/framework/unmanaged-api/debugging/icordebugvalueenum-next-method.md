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
ms.openlocfilehash: db1721fed6414310556ceac493275e069a781ac8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397138"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="7e680-102">Método ICorDebugValueEnum::Next</span><span class="sxs-lookup"><span data-stu-id="7e680-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="7e680-103">Obtém o número especificado de instâncias "ICorDebugValue" da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="7e680-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e680-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e680-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e680-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e680-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7e680-106">no O número de `ICorDebugValue` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="7e680-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="7e680-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="7e680-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7e680-108">fora Aponta para o número de `ICorDebugValue` instâncias realmente retornadas.</span><span class="sxs-lookup"><span data-stu-id="7e680-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="7e680-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="7e680-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e680-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e680-110">Requirements</span></span>  
 <span data-ttu-id="7e680-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e680-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e680-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e680-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e680-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e680-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e680-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e680-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e680-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e680-115">See also</span></span>
