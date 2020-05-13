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
ms.openlocfilehash: c9999961ec20a31cf82d5ad60104bcdd04c340d1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210170"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="d77cd-102">Método ICorDebugHeapSegmentEnum::Next</span><span class="sxs-lookup"><span data-stu-id="d77cd-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="d77cd-103">Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d77cd-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d77cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d77cd-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d77cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d77cd-105">Parameters</span></span>  
 <span data-ttu-id="d77cd-106">celt</span><span class="sxs-lookup"><span data-stu-id="d77cd-106">celt</span></span>  
 <span data-ttu-id="d77cd-107">no O número de segmentos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="d77cd-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="d77cd-108">segmentos</span><span class="sxs-lookup"><span data-stu-id="d77cd-108">segments</span></span>  
 <span data-ttu-id="d77cd-109">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [COR_HEAPOBJECT](cor-heapobject-structure.md) que fornece informações sobre uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d77cd-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="d77cd-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="d77cd-110">pceltFetched</span></span>  
 <span data-ttu-id="d77cd-111">fora Um ponteiro para o número de objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) realmente retornados em `segments` .</span><span class="sxs-lookup"><span data-stu-id="d77cd-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="d77cd-112">Esse valor pode ser `null` se `celt` for 1.</span><span class="sxs-lookup"><span data-stu-id="d77cd-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d77cd-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="d77cd-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d77cd-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d77cd-114">Requirements</span></span>  
 <span data-ttu-id="d77cd-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d77cd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d77cd-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d77cd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d77cd-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d77cd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d77cd-118">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d77cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77cd-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="d77cd-119">See also</span></span>

- [<span data-ttu-id="d77cd-120">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="d77cd-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="d77cd-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d77cd-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
