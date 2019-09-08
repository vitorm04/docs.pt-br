---
title: Enumeração ASM_CACHE_FLAGS
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e3e9da3db71d3e24b2a60ff032a631680055b88
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795281"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="6531a-102">Enumeração ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6531a-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="6531a-103">Indica a origem de um assembly que é representado por [IAssemblyCacheItem](iassemblycacheitem-interface.md) no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="6531a-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6531a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6531a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6531a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6531a-105">Members</span></span>  
  
|<span data-ttu-id="6531a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6531a-106">Member</span></span>|<span data-ttu-id="6531a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6531a-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="6531a-108">Enumera o cache de assemblies pré-compilados usando NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="6531a-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="6531a-109">Enumera o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="6531a-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="6531a-110">Enumera os assemblies que foram baixados sob demanda ou que foram copiados por sombra.</span><span class="sxs-lookup"><span data-stu-id="6531a-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="6531a-111">Indica que a função [GetCachePath](getcachepath-function.md) deve retornar o caminho para o cache de assembly global para a versão 2,0 do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6531a-111">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="6531a-112">Significativo apenas no contexto de uma chamada para [GetCachePath](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="6531a-112">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="6531a-113">Indica que a função [GetCachePath](getcachepath-function.md) deve retornar o caminho para o cache de assembly global para CLR versão 4.</span><span class="sxs-lookup"><span data-stu-id="6531a-113">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="6531a-114">Significativo apenas no contexto de uma chamada para [GetCachePath](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="6531a-114">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6531a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6531a-115">Requirements</span></span>  
 <span data-ttu-id="6531a-116">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6531a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6531a-117">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6531a-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6531a-118">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6531a-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6531a-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6531a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6531a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6531a-120">See also</span></span>

- [<span data-ttu-id="6531a-121">Função GetCachePath</span><span class="sxs-lookup"><span data-stu-id="6531a-121">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="6531a-122">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="6531a-122">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="6531a-123">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="6531a-123">Fusion Enumerations</span></span>](fusion-enumerations.md)
