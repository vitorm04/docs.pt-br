---
title: Método ICorDebugObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a1c0f7deb2ef24893530797b4507e2dcc540ad2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757051"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="9ce55-102">Método ICorDebugObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="9ce55-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="9ce55-103">Obtém os endereços virtuais (relacionados RVAs) do número especificado de objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="9ce55-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ce55-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ce55-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ce55-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9ce55-106">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="9ce55-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="9ce55-107">[out] Uma matriz de ponteiros, cada qual apontando para um objeto CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="9ce55-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9ce55-108">[out] Ponteiro para o número de objetos, na verdade, é retornado.</span><span class="sxs-lookup"><span data-stu-id="9ce55-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="9ce55-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="9ce55-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce55-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ce55-110">Requirements</span></span>  
 <span data-ttu-id="9ce55-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ce55-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ce55-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ce55-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ce55-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ce55-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ce55-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ce55-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce55-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ce55-115">See also</span></span>
