---
title: Método ICorDebugHeapSegmentEnum::Next
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31e75a11ec94614b1b9d7bd16acce447a494cdec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756776"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="8130d-102">Método ICorDebugHeapSegmentEnum::Next</span><span class="sxs-lookup"><span data-stu-id="8130d-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="8130d-103">Obtém o número especificado de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que contêm informações sobre regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8130d-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8130d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8130d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8130d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8130d-105">Parameters</span></span>  
 <span data-ttu-id="8130d-106">celt</span><span class="sxs-lookup"><span data-stu-id="8130d-106">celt</span></span>  
 <span data-ttu-id="8130d-107">[in] O número de segmentos a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="8130d-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="8130d-108">segmentos</span><span class="sxs-lookup"><span data-stu-id="8130d-108">segments</span></span>  
 <span data-ttu-id="8130d-109">[out] Uma matriz de ponteiros, cada qual apontando para um [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objeto que fornece informações sobre uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8130d-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="8130d-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="8130d-110">pceltFetched</span></span>  
 <span data-ttu-id="8130d-111">[out] Um ponteiro para o número de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos, na verdade, são retornados em `segments`.</span><span class="sxs-lookup"><span data-stu-id="8130d-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="8130d-112">Esse valor pode ser `null` se `celt` é 1.</span><span class="sxs-lookup"><span data-stu-id="8130d-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8130d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8130d-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8130d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8130d-114">Requirements</span></span>  
 <span data-ttu-id="8130d-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8130d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8130d-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8130d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8130d-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8130d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8130d-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8130d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8130d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8130d-119">See also</span></span>

- [<span data-ttu-id="8130d-120">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="8130d-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="8130d-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8130d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
