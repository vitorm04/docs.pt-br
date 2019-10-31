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
ms.openlocfilehash: 85ac976daec8fd76ee21012a30611235609f4b34
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109488"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="e1674-102">Enumeração ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e1674-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="e1674-103">Indica a origem de um assembly que é representado por [IAssemblyCacheItem](iassemblycacheitem-interface.md) no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e1674-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1674-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1674-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e1674-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e1674-105">Members</span></span>  
  
|<span data-ttu-id="e1674-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e1674-106">Member</span></span>|<span data-ttu-id="e1674-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1674-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="e1674-108">Enumera o cache de assemblies pré-compilados usando NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="e1674-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="e1674-109">Enumera o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e1674-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="e1674-110">Enumera os assemblies que foram baixados sob demanda ou que foram copiados por sombra.</span><span class="sxs-lookup"><span data-stu-id="e1674-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="e1674-111">Indica que a função [GetCachePath](getcachepath-function.md) deve retornar o caminho para o cache de assembly global para a versão 2,0 do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e1674-111">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="e1674-112">Significativo apenas no contexto de uma chamada para [GetCachePath](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="e1674-112">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="e1674-113">Indica que a função [GetCachePath](getcachepath-function.md) deve retornar o caminho para o cache de assembly global para CLR versão 4.</span><span class="sxs-lookup"><span data-stu-id="e1674-113">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="e1674-114">Significativo apenas no contexto de uma chamada para [GetCachePath](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="e1674-114">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1674-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1674-115">Requirements</span></span>  
 <span data-ttu-id="e1674-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1674-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1674-117">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e1674-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e1674-118">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e1674-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1674-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1674-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1674-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1674-120">See also</span></span>

- [<span data-ttu-id="e1674-121">Função GetCachePath</span><span class="sxs-lookup"><span data-stu-id="e1674-121">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="e1674-122">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="e1674-122">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="e1674-123">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="e1674-123">Fusion Enumerations</span></span>](fusion-enumerations.md)
