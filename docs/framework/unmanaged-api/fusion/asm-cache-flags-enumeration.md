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
ms.openlocfilehash: 619643eb50abc75fd10d59b38767013b2617c8cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077753"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="e17ad-102">Enumeração ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e17ad-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="e17ad-103">Indica a origem de um assembly que é representado por [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e17ad-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e17ad-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e17ad-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e17ad-105">Members</span></span>  
  
|<span data-ttu-id="e17ad-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e17ad-106">Member</span></span>|<span data-ttu-id="e17ad-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e17ad-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="e17ad-108">Enumera o cache de assemblies pré-compilados usando Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e17ad-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="e17ad-109">Enumera o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e17ad-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="e17ad-110">Enumera os assemblies que foram baixadas sob demanda ou que foram copiados em sombra.</span><span class="sxs-lookup"><span data-stu-id="e17ad-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="e17ad-111">Indica que o [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) função deve retornar o caminho para o cache de assembly global para o common language runtime (CLR) versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="e17ad-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="e17ad-112">Significativos apenas no contexto de uma chamada para [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="e17ad-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="e17ad-113">Indica que o [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) função deve retornar o caminho para o cache de assembly global para a versão 4 do CLR.</span><span class="sxs-lookup"><span data-stu-id="e17ad-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="e17ad-114">Significativos apenas no contexto de uma chamada para [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="e17ad-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e17ad-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e17ad-115">Requirements</span></span>  
 <span data-ttu-id="e17ad-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e17ad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e17ad-117">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e17ad-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e17ad-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e17ad-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e17ad-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e17ad-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e17ad-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e17ad-120">See also</span></span>

- [<span data-ttu-id="e17ad-121">Função GetCachePath</span><span class="sxs-lookup"><span data-stu-id="e17ad-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)
- [<span data-ttu-id="e17ad-122">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="e17ad-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
- [<span data-ttu-id="e17ad-123">Enumerações Fusion</span><span class="sxs-lookup"><span data-stu-id="e17ad-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
