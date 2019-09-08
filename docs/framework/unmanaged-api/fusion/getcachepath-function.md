---
title: Função GetCachePath
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c28f32a4b24393483241bd2d7d6f550b8b65ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796898"
---
# <a name="getcachepath-function"></a><span data-ttu-id="d4551-102">Função GetCachePath</span><span class="sxs-lookup"><span data-stu-id="d4551-102">GetCachePath Function</span></span>
<span data-ttu-id="d4551-103">Obtém o caminho para o assembly armazenado em cache, usando os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="d4551-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4551-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4551-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4551-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d4551-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="d4551-106">no Um valor [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) que indica a origem do assembly armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="d4551-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="d4551-107">fora O ponteiro retornado para o caminho.</span><span class="sxs-lookup"><span data-stu-id="d4551-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="d4551-108">[entrada, saída] O comprimento máximo solicitado de `pwzCachePath`e, após o retorno, o comprimento real `pwzCachePath`de.</span><span class="sxs-lookup"><span data-stu-id="d4551-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4551-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4551-109">Requirements</span></span>  
 <span data-ttu-id="d4551-110">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4551-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4551-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d4551-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d4551-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4551-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4551-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4551-113">See also</span></span>

- [<span data-ttu-id="d4551-114">Enumeração ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d4551-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="d4551-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="d4551-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
