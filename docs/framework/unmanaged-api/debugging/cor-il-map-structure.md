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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9676730a4f11ed77996b7a4aab4e538aba9b53c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407356"
---
# <a name="corilmap-structure"></a><span data-ttu-id="17c48-102">Estrutura COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="17c48-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="17c48-103">Especifica mudanças no deslocamento relativo de uma função.</span><span class="sxs-lookup"><span data-stu-id="17c48-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17c48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17c48-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="17c48-105">Membros</span><span class="sxs-lookup"><span data-stu-id="17c48-105">Members</span></span>  
  
|<span data-ttu-id="17c48-106">Membro</span><span class="sxs-lookup"><span data-stu-id="17c48-106">Member</span></span>|<span data-ttu-id="17c48-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="17c48-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="17c48-108">O antigo Microsoft intermediate language (MSIL) deslocamento relativo ao início da função.</span><span class="sxs-lookup"><span data-stu-id="17c48-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="17c48-109">O deslocamento MSIL novo relativo ao início da função.</span><span class="sxs-lookup"><span data-stu-id="17c48-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="17c48-110">`true` Se o mapeamento é conhecido por ser preciso; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="17c48-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17c48-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="17c48-111">Remarks</span></span>  
 <span data-ttu-id="17c48-112">O formato do mapa é da seguinte maneira: O depurador assumirá que `oldOffset` refere-se a um deslocamento MSIL dentro do código MSIL original, não modificado.</span><span class="sxs-lookup"><span data-stu-id="17c48-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="17c48-113">O `newOffset` parâmetro refere-se para o deslocamento MSIL correspondente no código instrumentado, novo.</span><span class="sxs-lookup"><span data-stu-id="17c48-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="17c48-114">Para passar para funcionar corretamente, os seguintes requisitos devem ser atendidos:</span><span class="sxs-lookup"><span data-stu-id="17c48-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
-   <span data-ttu-id="17c48-115">O mapa deve ser classificado em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="17c48-115">The map should be sorted in ascending order.</span></span>  
  
-   <span data-ttu-id="17c48-116">Não deve ser reordenado código MSIL instrumentado.</span><span class="sxs-lookup"><span data-stu-id="17c48-116">Instrumented MSIL code should not be reordered.</span></span>  
  
-   <span data-ttu-id="17c48-117">Código MSIL original não deve ser removido.</span><span class="sxs-lookup"><span data-stu-id="17c48-117">Original MSIL code should not be removed.</span></span>  
  
-   <span data-ttu-id="17c48-118">O mapa deve incluir as entradas para todos os pontos de sequência do arquivo de programa (PDB) de banco de dados do mapa.</span><span class="sxs-lookup"><span data-stu-id="17c48-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="17c48-119">O mapa não interpolar entradas ausentes.</span><span class="sxs-lookup"><span data-stu-id="17c48-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="17c48-120">O exemplo a seguir mostra um mapa e seus resultados.</span><span class="sxs-lookup"><span data-stu-id="17c48-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="17c48-121">Mapa:</span><span class="sxs-lookup"><span data-stu-id="17c48-121">Map:</span></span>  
  
-   <span data-ttu-id="17c48-122">deslocamento antigo 0, 0 deslocamento novo</span><span class="sxs-lookup"><span data-stu-id="17c48-122">0 old offset, 0 new offset</span></span>  
  
-   <span data-ttu-id="17c48-123">deslocamento antigo 5, 10 deslocamento novo</span><span class="sxs-lookup"><span data-stu-id="17c48-123">5 old offset, 10 new offset</span></span>  
  
-   <span data-ttu-id="17c48-124">deslocamento antigo 9, 20 de deslocamento de novo</span><span class="sxs-lookup"><span data-stu-id="17c48-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="17c48-125">Resultados:</span><span class="sxs-lookup"><span data-stu-id="17c48-125">Results:</span></span>  
  
-   <span data-ttu-id="17c48-126">Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para um novo deslocamento de 0.</span><span class="sxs-lookup"><span data-stu-id="17c48-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
-   <span data-ttu-id="17c48-127">Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento de 10.</span><span class="sxs-lookup"><span data-stu-id="17c48-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
-   <span data-ttu-id="17c48-128">Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.</span><span class="sxs-lookup"><span data-stu-id="17c48-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
-   <span data-ttu-id="17c48-129">Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o antigo deslocamento de 0.</span><span class="sxs-lookup"><span data-stu-id="17c48-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
-   <span data-ttu-id="17c48-130">Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.</span><span class="sxs-lookup"><span data-stu-id="17c48-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
-   <span data-ttu-id="17c48-131">Um novo deslocamento de 20 ou maior será mapeado para deslocamento antigo 9.</span><span class="sxs-lookup"><span data-stu-id="17c48-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17c48-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17c48-132">Requirements</span></span>  
 <span data-ttu-id="17c48-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17c48-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17c48-134">**Cabeçalho:** CorDebug.idl, Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="17c48-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="17c48-135">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17c48-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17c48-136">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17c48-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c48-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17c48-137">See Also</span></span>  
 [<span data-ttu-id="17c48-138">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="17c48-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="17c48-139">Depuração</span><span class="sxs-lookup"><span data-stu-id="17c48-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
