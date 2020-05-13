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
ms.openlocfilehash: 5d0b231b4014e60a9e8778c6b9d6ed7758b2d8c5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208467"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="6efab-102">Método ICorDebugHeapEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6efab-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="6efab-103">Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6efab-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6efab-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6efab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6efab-105">Parameters</span></span>  
 <span data-ttu-id="6efab-106">celt</span><span class="sxs-lookup"><span data-stu-id="6efab-106">celt</span></span>  
 <span data-ttu-id="6efab-107">no O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="6efab-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="6efab-108">objetos</span><span class="sxs-lookup"><span data-stu-id="6efab-108">objects</span></span>  
 <span data-ttu-id="6efab-109">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [COR_HEAPOBJECT](cor-heapobject-structure.md) que fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6efab-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="6efab-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="6efab-110">pceltFetched</span></span>  
 <span data-ttu-id="6efab-111">fora Um ponteiro para o número de objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) realmente retornados em `objects` .</span><span class="sxs-lookup"><span data-stu-id="6efab-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="6efab-112">Esse valor pode ser `null` se `celt` for 1.</span><span class="sxs-lookup"><span data-stu-id="6efab-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6efab-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="6efab-113">Remarks</span></span>  
 <span data-ttu-id="6efab-114">O `COR_HEAPOBJECT.type` campo é o identificador de uma interface com contada com referência aninhada.</span><span class="sxs-lookup"><span data-stu-id="6efab-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="6efab-115">Essa referência deve ser liberada pelo chamador de `ICorDebugHeapEnum::Next` .</span><span class="sxs-lookup"><span data-stu-id="6efab-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6efab-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6efab-116">Requirements</span></span>  
 <span data-ttu-id="6efab-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6efab-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6efab-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6efab-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6efab-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6efab-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6efab-120">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6efab-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efab-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="6efab-121">See also</span></span>

- [<span data-ttu-id="6efab-122">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="6efab-122">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="6efab-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6efab-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
