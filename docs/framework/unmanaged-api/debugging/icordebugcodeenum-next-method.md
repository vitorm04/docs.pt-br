---
title: Método ICorDebugCodeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e70f7ce9cd943fc3641eef710502ae7f50b369e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748550"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="8a241-102">Método ICorDebugCodeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="8a241-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="8a241-103">Obtém o número especificado de instâncias de "ICorDebugCode" de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="8a241-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a241-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a241-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a241-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a241-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8a241-106">[in] O número de `ICorDebugCode` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="8a241-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="8a241-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugCode` objeto.</span><span class="sxs-lookup"><span data-stu-id="8a241-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8a241-108">[out] Um ponteiro para o número de `ICorDebugCode` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="8a241-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="8a241-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="8a241-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a241-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a241-110">Requirements</span></span>  
 <span data-ttu-id="8a241-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a241-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a241-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a241-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a241-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a241-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a241-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a241-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a241-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a241-115">See also</span></span>
