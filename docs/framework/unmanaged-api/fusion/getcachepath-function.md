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
ms.openlocfilehash: cf23a8f1893aa0f992d554d3c7533c3dc42f4e95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150976"
---
# <a name="getcachepath-function"></a><span data-ttu-id="0d3a1-102">Função GetCachePath</span><span class="sxs-lookup"><span data-stu-id="0d3a1-102">GetCachePath Function</span></span>
<span data-ttu-id="0d3a1-103">Obtém o caminho para o assembly em cache, usando os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="0d3a1-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d3a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d3a1-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d3a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d3a1-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="0d3a1-106">[in] Uma [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) valor que indica a origem do assembly em cache.</span><span class="sxs-lookup"><span data-stu-id="0d3a1-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="0d3a1-107">[out] O ponteiro retornado para o caminho.</span><span class="sxs-lookup"><span data-stu-id="0d3a1-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="0d3a1-108">[no, out] O comprimento máximo solicitado de `pwzCachePath`e após o retorno, o comprimento real da `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="0d3a1-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d3a1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d3a1-109">Requirements</span></span>  
 <span data-ttu-id="0d3a1-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d3a1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d3a1-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0d3a1-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="0d3a1-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0d3a1-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d3a1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d3a1-113">See also</span></span>

- [<span data-ttu-id="0d3a1-114">Enumeração ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0d3a1-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [<span data-ttu-id="0d3a1-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="0d3a1-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
