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
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178695"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="0814f-102">Método ICorDebugObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="0814f-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="0814f-103">Obtém os endereços virtuais relativos (RVAs) do número especificado de objetos da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="0814f-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0814f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0814f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0814f-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="0814f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0814f-106">[em] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="0814f-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="0814f-107">[fora] Uma matriz de ponteiros, cada um dos quais aponta para um objeto CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="0814f-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0814f-108">[fora] Ponteiro para o número de objetos realmente retornado.</span><span class="sxs-lookup"><span data-stu-id="0814f-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="0814f-109">Este valor pode `celt` ser nulo se for um.</span><span class="sxs-lookup"><span data-stu-id="0814f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0814f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0814f-110">Requirements</span></span>  
 <span data-ttu-id="0814f-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0814f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0814f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0814f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0814f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0814f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0814f-114">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0814f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0814f-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="0814f-115">See also</span></span>
