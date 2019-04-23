---
title: Enumeração COR_PRF_JIT_CACHE
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cdbe36403f830926d611ffdc655d82ea25ddeef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144788"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="e245f-102">Enumeração COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="e245f-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="e245f-103">Indica o resultado de uma busca de função armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="e245f-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e245f-104">`COR_PRF_CACHED_FUNCTION_FOUND` tem um valor de zero, então, `COR_PRF_JIT_CACHE` não pode ser usado como um substituto booliano.</span><span class="sxs-lookup"><span data-stu-id="e245f-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e245f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e245f-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="e245f-106">Membros</span><span class="sxs-lookup"><span data-stu-id="e245f-106">Members</span></span>  
  
|<span data-ttu-id="e245f-107">Membro</span><span class="sxs-lookup"><span data-stu-id="e245f-107">Member</span></span>|<span data-ttu-id="e245f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e245f-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="e245f-109">A função foi encontrado pela pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e245f-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="e245f-110">A pesquisa não encontrou a função.</span><span class="sxs-lookup"><span data-stu-id="e245f-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e245f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e245f-111">Requirements</span></span>  
 <span data-ttu-id="e245f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e245f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e245f-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e245f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e245f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e245f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e245f-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e245f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e245f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e245f-116">See also</span></span>

- [<span data-ttu-id="e245f-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="e245f-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
