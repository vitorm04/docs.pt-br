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
ms.openlocfilehash: 3d4e44eefaf99a40b9c4f1c45e7dd81192f8b607
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904267"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="5bfa5-102">Método ICorDebugHeapSegmentEnum::Next</span><span class="sxs-lookup"><span data-stu-id="5bfa5-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="5bfa5-103">Obtém o número especificado de instâncias de [COR_SEGMENT](cor-segment-structure.md) que contêm informações sobre regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5bfa5-103">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfa5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bfa5-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bfa5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5bfa5-105">Parameters</span></span>  
 <span data-ttu-id="5bfa5-106">celt</span><span class="sxs-lookup"><span data-stu-id="5bfa5-106">celt</span></span>  
 <span data-ttu-id="5bfa5-107">no O número de segmentos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="5bfa5-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="5bfa5-108">segmentos</span><span class="sxs-lookup"><span data-stu-id="5bfa5-108">segments</span></span>  
 <span data-ttu-id="5bfa5-109">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [COR_SEGMENT](cor-segment-structure.md) que fornece informações sobre uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5bfa5-109">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="5bfa5-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="5bfa5-110">pceltFetched</span></span>  
 <span data-ttu-id="5bfa5-111">fora Um ponteiro para o número de objetos [COR_SEGMENT](cor-segment-structure.md) realmente retornados em `segments` .</span><span class="sxs-lookup"><span data-stu-id="5bfa5-111">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="5bfa5-112">Esse valor pode ser `null` se `celt` for 1.</span><span class="sxs-lookup"><span data-stu-id="5bfa5-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bfa5-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bfa5-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bfa5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bfa5-114">Requirements</span></span>  
 <span data-ttu-id="5bfa5-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bfa5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bfa5-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bfa5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bfa5-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bfa5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bfa5-118">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bfa5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfa5-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="5bfa5-119">See also</span></span>

- [<span data-ttu-id="5bfa5-120">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="5bfa5-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="5bfa5-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5bfa5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
