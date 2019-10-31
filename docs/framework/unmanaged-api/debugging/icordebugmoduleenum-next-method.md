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
ms.openlocfilehash: 6c4262c18e4efcbbca1b3e2a327fec7d4b609a31
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096923"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="6257e-102">Método ICorDebugModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6257e-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="6257e-103">Obtém o número de instâncias "ICorDebugModule" especificadas por `celt` da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="6257e-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6257e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6257e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6257e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6257e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6257e-106">no O número de instâncias de `ICorDebugModule` a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="6257e-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="6257e-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="6257e-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6257e-108">fora Aponta para o número de instâncias de `ICorDebugModule` retornadas na verdade.</span><span class="sxs-lookup"><span data-stu-id="6257e-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="6257e-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="6257e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6257e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6257e-110">Requirements</span></span>  
 <span data-ttu-id="6257e-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6257e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6257e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6257e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6257e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6257e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6257e-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6257e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6257e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6257e-115">See also</span></span>
