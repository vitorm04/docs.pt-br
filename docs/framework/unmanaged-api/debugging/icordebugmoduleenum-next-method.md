---
title: Método ICorDebugModuleEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: d7ad4a6b25fe6d53ab0b21066345451ae7c22c16
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213316"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="c43d4-102">Método ICorDebugModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="c43d4-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="c43d4-103">Obtém o número de instâncias "ICorDebugModule" especificadas pelo `celt` da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="c43d4-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c43d4-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c43d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c43d4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c43d4-106">no O número de `ICorDebugModule` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="c43d4-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="c43d4-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um `ICorDebugModule` objeto.</span><span class="sxs-lookup"><span data-stu-id="c43d4-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c43d4-108">fora Aponta para o número de `ICorDebugModule` instâncias realmente retornadas.</span><span class="sxs-lookup"><span data-stu-id="c43d4-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="c43d4-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="c43d4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c43d4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c43d4-110">Requirements</span></span>  
 <span data-ttu-id="c43d4-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c43d4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c43d4-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c43d4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c43d4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c43d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c43d4-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c43d4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43d4-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="c43d4-115">See also</span></span>
