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
ms.openlocfilehash: 13e1468ef5a48f18910c1f8082cdd7c4849da14a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132690"
---
# <a name="getcachepath-function"></a><span data-ttu-id="bcd04-102">Função GetCachePath</span><span class="sxs-lookup"><span data-stu-id="bcd04-102">GetCachePath Function</span></span>
<span data-ttu-id="bcd04-103">Obtém o caminho para o assembly armazenado em cache, usando os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="bcd04-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcd04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcd04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcd04-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bcd04-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="bcd04-106">no Um valor [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) que indica a origem do assembly armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="bcd04-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="bcd04-107">fora O ponteiro retornado para o caminho.</span><span class="sxs-lookup"><span data-stu-id="bcd04-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="bcd04-108">[entrada, saída] O comprimento máximo solicitado de `pwzCachePath`e, após o retorno, o comprimento real de `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="bcd04-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcd04-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bcd04-109">Requirements</span></span>  
 <span data-ttu-id="bcd04-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcd04-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcd04-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bcd04-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bcd04-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcd04-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd04-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcd04-113">See also</span></span>

- [<span data-ttu-id="bcd04-114">Enumeração ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="bcd04-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="bcd04-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="bcd04-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
