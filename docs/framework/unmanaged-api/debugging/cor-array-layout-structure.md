---
title: Estrutura COR_ARRAY_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a5a5bb26912c87cdf37ba0d8f0cee1cf1ffa97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142006"
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="b8839-102">Estrutura COR_ARRAY_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="b8839-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="b8839-103">Fornece informações sobre o layout de um objeto matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="b8839-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8839-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8839-104">Syntax</span></span>  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="b8839-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b8839-105">Members</span></span>  
  
|<span data-ttu-id="b8839-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b8839-106">Member</span></span>|<span data-ttu-id="b8839-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8839-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="b8839-108">O identificador do tipo de objetos que contém a matriz.</span><span class="sxs-lookup"><span data-stu-id="b8839-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="b8839-109">Um valor de enumeração CorElementType que indica se o componente é uma referência de coleta de lixo, uma classe de valor ou um primitivo.</span><span class="sxs-lookup"><span data-stu-id="b8839-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="b8839-110">O deslocamento para o primeiro elemento na matriz.</span><span class="sxs-lookup"><span data-stu-id="b8839-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="b8839-111">O tamanho de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="b8839-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="b8839-112">O deslocamento para o número de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="b8839-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="b8839-113">O tamanho de classificação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="b8839-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="b8839-114">O número de classificações na matriz.</span><span class="sxs-lookup"><span data-stu-id="b8839-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="b8839-115">O deslocamento no qual iniciar as classificações.</span><span class="sxs-lookup"><span data-stu-id="b8839-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8839-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8839-116">Remarks</span></span>  
 <span data-ttu-id="b8839-117">O `rankSize` campo especifica o tamanho de uma classificação em uma matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="b8839-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="b8839-118">É preciso para matrizes unidimensionais também.</span><span class="sxs-lookup"><span data-stu-id="b8839-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="b8839-119">O valor de `numRanks` é 1 para uma matriz unidimensional e `N` para uma matriz multidimensional de `N` dimensões.</span><span class="sxs-lookup"><span data-stu-id="b8839-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8839-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8839-120">Requirements</span></span>  
 <span data-ttu-id="b8839-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8839-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8839-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8839-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8839-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8839-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8839-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8839-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8839-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8839-125">See also</span></span>

- [<span data-ttu-id="b8839-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="b8839-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b8839-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="b8839-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
