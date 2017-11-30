---
title: "Função GetCachePath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: GetCachePath
helpviewer_keywords: GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 924482bf34d53d3d7144c4bae93a00a8f8d2ad4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="getcachepath-function"></a><span data-ttu-id="167f9-102">Função GetCachePath</span><span class="sxs-lookup"><span data-stu-id="167f9-102">GetCachePath Function</span></span>
<span data-ttu-id="167f9-103">Obtém o caminho para o assembly em cache, usando os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="167f9-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="167f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="167f9-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="167f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="167f9-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="167f9-106">[in] Um [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) valor que indica a origem do assembly em cache.</span><span class="sxs-lookup"><span data-stu-id="167f9-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="167f9-107">[out] O ponteiro retornado para o caminho.</span><span class="sxs-lookup"><span data-stu-id="167f9-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="167f9-108">[out no] O tamanho máximo solicitado da `pwzCachePath`e no retorno, o comprimento real da `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="167f9-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="167f9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="167f9-109">Requirements</span></span>  
 <span data-ttu-id="167f9-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="167f9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="167f9-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="167f9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="167f9-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="167f9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167f9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="167f9-113">See Also</span></span>  
 [<span data-ttu-id="167f9-114">Enumeração ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="167f9-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="167f9-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="167f9-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
