---
title: Estrutura COR_IL_MAP
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: c37f039d9636854c464e7981693c573bd60deab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132341"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="642ad-102">Estrutura COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="642ad-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="642ad-103">Especifica mudanças no deslocamento relativo de uma função.</span><span class="sxs-lookup"><span data-stu-id="642ad-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="642ad-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="642ad-105">Membros</span><span class="sxs-lookup"><span data-stu-id="642ad-105">Members</span></span>  
  
|<span data-ttu-id="642ad-106">Membro</span><span class="sxs-lookup"><span data-stu-id="642ad-106">Member</span></span>|<span data-ttu-id="642ad-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="642ad-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="642ad-108">O antigo deslocamento da MSIL (Microsoft Intermediate Language) relativo ao início da função.</span><span class="sxs-lookup"><span data-stu-id="642ad-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="642ad-109">O novo deslocamento MSIL relativo ao início da função.</span><span class="sxs-lookup"><span data-stu-id="642ad-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="642ad-110">`true` se é conhecido que o mapeamento seja preciso; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="642ad-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="642ad-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="642ad-111">Remarks</span></span>  
 <span data-ttu-id="642ad-112">O formato do mapa é o seguinte: o depurador irá supor que `oldOffset` se refere a um deslocamento MSIL dentro do código MSIL original e não modificado.</span><span class="sxs-lookup"><span data-stu-id="642ad-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="642ad-113">O parâmetro `newOffset` refere-se ao deslocamento MSIL correspondente dentro do novo código instrumentado.</span><span class="sxs-lookup"><span data-stu-id="642ad-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="642ad-114">Para que a depuração funcione corretamente, os requisitos a seguir devem ser atendidos:</span><span class="sxs-lookup"><span data-stu-id="642ad-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="642ad-115">O mapa deve ser classificado em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="642ad-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="642ad-116">O código MSIL instrumentado não deve ser reordenado.</span><span class="sxs-lookup"><span data-stu-id="642ad-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="642ad-117">O código MSIL original não deve ser removido.</span><span class="sxs-lookup"><span data-stu-id="642ad-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="642ad-118">O mapa deve incluir entradas para mapear todos os pontos de sequência do arquivo de banco de dados do programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="642ad-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="642ad-119">O mapa não interpola as entradas ausentes.</span><span class="sxs-lookup"><span data-stu-id="642ad-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="642ad-120">O exemplo a seguir mostra um mapa e seus resultados.</span><span class="sxs-lookup"><span data-stu-id="642ad-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="642ad-121">Mapeada</span><span class="sxs-lookup"><span data-stu-id="642ad-121">Map:</span></span>  
  
- <span data-ttu-id="642ad-122">0 deslocamento antigo, 0 deslocamento novo</span><span class="sxs-lookup"><span data-stu-id="642ad-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="642ad-123">5 deslocamento antigo, 10 novos deslocamentos</span><span class="sxs-lookup"><span data-stu-id="642ad-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="642ad-124">9 deslocamento antigo, 20 deslocamento novo</span><span class="sxs-lookup"><span data-stu-id="642ad-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="642ad-125">Da</span><span class="sxs-lookup"><span data-stu-id="642ad-125">Results:</span></span>  
  
- <span data-ttu-id="642ad-126">Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para um novo deslocamento de 0.</span><span class="sxs-lookup"><span data-stu-id="642ad-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="642ad-127">Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento 10.</span><span class="sxs-lookup"><span data-stu-id="642ad-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="642ad-128">Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.</span><span class="sxs-lookup"><span data-stu-id="642ad-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="642ad-129">Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o deslocamento antigo 0.</span><span class="sxs-lookup"><span data-stu-id="642ad-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="642ad-130">Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.</span><span class="sxs-lookup"><span data-stu-id="642ad-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="642ad-131">Um novo deslocamento de 20 ou mais será mapeado para o deslocamento antigo 9.</span><span class="sxs-lookup"><span data-stu-id="642ad-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="642ad-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="642ad-132">Requirements</span></span>  
 <span data-ttu-id="642ad-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="642ad-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="642ad-134">**Cabeçalho:** CorDebug. idl, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="642ad-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="642ad-135">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="642ad-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="642ad-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="642ad-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642ad-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="642ad-137">See also</span></span>

- [<span data-ttu-id="642ad-138">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="642ad-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="642ad-139">Depuração</span><span class="sxs-lookup"><span data-stu-id="642ad-139">Debugging</span></span>](index.md)
