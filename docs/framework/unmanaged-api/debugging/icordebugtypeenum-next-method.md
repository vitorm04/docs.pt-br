---
title: Método ICorDebugTypeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: 83adea3d659eea6d4af9ae364aad18df67e69c03
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396614"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="3e10c-102">Método ICorDebugTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="3e10c-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="3e10c-103">Obtém o número de instâncias "ICorDebugType" especificadas pelo `celt` da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="3e10c-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e10c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e10c-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e10c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e10c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3e10c-106">no O número de `ICorDebugType` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="3e10c-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3e10c-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um `ICorDebugType` objeto.</span><span class="sxs-lookup"><span data-stu-id="3e10c-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3e10c-108">fora Aponta para o número de `ICorDebugType` instâncias realmente retornadas.</span><span class="sxs-lookup"><span data-stu-id="3e10c-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="3e10c-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="3e10c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e10c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e10c-110">Requirements</span></span>  
 <span data-ttu-id="3e10c-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e10c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e10c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e10c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e10c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e10c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e10c-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e10c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e10c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="3e10c-115">See also</span></span>
