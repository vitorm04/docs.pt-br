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
ms.openlocfilehash: 1beb69bfaad9acb9c269ad8becb81bea64edb6a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138464"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="13a11-102">Método ICorDebugHeapEnum::Next</span><span class="sxs-lookup"><span data-stu-id="13a11-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="13a11-103">Obtém o número especificado de instâncias [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="13a11-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13a11-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a11-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13a11-105">Parameters</span></span>  
 <span data-ttu-id="13a11-106">celt</span><span class="sxs-lookup"><span data-stu-id="13a11-106">celt</span></span>  
 <span data-ttu-id="13a11-107">no O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="13a11-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="13a11-108">objetos</span><span class="sxs-lookup"><span data-stu-id="13a11-108">objects</span></span>  
 <span data-ttu-id="13a11-109">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) que fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="13a11-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="13a11-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="13a11-110">pceltFetched</span></span>  
 <span data-ttu-id="13a11-111">fora Um ponteiro para o número de objetos [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) realmente retornados em `objects`.</span><span class="sxs-lookup"><span data-stu-id="13a11-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="13a11-112">Esse valor pode ser `null` se `celt` for 1.</span><span class="sxs-lookup"><span data-stu-id="13a11-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a11-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="13a11-113">Remarks</span></span>  
 <span data-ttu-id="13a11-114">O campo `COR_HEAPOBJECT.type` é o identificador de uma interface COM contada COM referência aninhada.</span><span class="sxs-lookup"><span data-stu-id="13a11-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="13a11-115">Essa referência deve ser liberada pelo chamador de `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="13a11-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a11-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13a11-116">Requirements</span></span>  
 <span data-ttu-id="13a11-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a11-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a11-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13a11-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13a11-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13a11-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13a11-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a11-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a11-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13a11-121">See also</span></span>

- [<span data-ttu-id="13a11-122">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="13a11-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [<span data-ttu-id="13a11-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="13a11-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
