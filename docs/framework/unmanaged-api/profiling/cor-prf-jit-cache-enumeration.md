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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144788"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="b293a-102">Enumeração COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="b293a-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="b293a-103">Indica o resultado de uma busca de função armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="b293a-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  `COR_PRF_CACHED_FUNCTION_FOUND` <span data-ttu-id="b293a-104">tem um valor de zero, então, `COR_PRF_JIT_CACHE` não pode ser usado como um substituto booliano.</span><span class="sxs-lookup"><span data-stu-id="b293a-104">has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b293a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b293a-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="b293a-106">Membros</span><span class="sxs-lookup"><span data-stu-id="b293a-106">Members</span></span>  
  
|<span data-ttu-id="b293a-107">Membro</span><span class="sxs-lookup"><span data-stu-id="b293a-107">Member</span></span>|<span data-ttu-id="b293a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b293a-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="b293a-109">A função foi encontrado pela pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b293a-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="b293a-110">A pesquisa não encontrou a função.</span><span class="sxs-lookup"><span data-stu-id="b293a-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b293a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b293a-111">Requirements</span></span>  
 <span data-ttu-id="b293a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b293a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b293a-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b293a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b293a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b293a-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b293a-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b293a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b293a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b293a-116">See also</span></span>

- [<span data-ttu-id="b293a-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="b293a-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
