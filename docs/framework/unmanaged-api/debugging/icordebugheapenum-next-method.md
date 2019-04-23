---
title: Método ICorDebugHeapEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd993eb26f26818117a20d376c3331f88c46b26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214345"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="68863-102">Método ICorDebugHeapEnum::Next</span><span class="sxs-lookup"><span data-stu-id="68863-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="68863-103">Obtém o número especificado de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="68863-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68863-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68863-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68863-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="68863-105">Parameters</span></span>  
 <span data-ttu-id="68863-106">celt</span><span class="sxs-lookup"><span data-stu-id="68863-106">celt</span></span>  
 <span data-ttu-id="68863-107">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="68863-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="68863-108">objetos</span><span class="sxs-lookup"><span data-stu-id="68863-108">objects</span></span>  
 <span data-ttu-id="68863-109">[out] Uma matriz de ponteiros, cada qual apontando para um [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objeto que fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="68863-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="68863-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="68863-110">pceltFetched</span></span>  
 <span data-ttu-id="68863-111">[out] Um ponteiro para o número de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos, na verdade, são retornados em `objects`.</span><span class="sxs-lookup"><span data-stu-id="68863-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="68863-112">Esse valor pode ser `null` se `celt` é 1.</span><span class="sxs-lookup"><span data-stu-id="68863-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68863-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="68863-113">Remarks</span></span>  
 <span data-ttu-id="68863-114">O `COR_HEAPOBJECT.type` campo é o identificador de uma interface de COM contado por referência aninhada.</span><span class="sxs-lookup"><span data-stu-id="68863-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="68863-115">Essa referência deve ser liberada, o chamador de `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="68863-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68863-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68863-116">Requirements</span></span>  
 <span data-ttu-id="68863-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68863-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68863-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68863-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68863-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68863-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68863-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68863-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68863-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68863-121">See also</span></span>

- [<span data-ttu-id="68863-122">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="68863-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [<span data-ttu-id="68863-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="68863-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
