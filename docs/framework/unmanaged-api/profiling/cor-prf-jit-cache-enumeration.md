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
ms.openlocfilehash: d19d7ed2262db6d3c6e7f15db0e96da52f86db4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500852"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="d2af0-102">Enumeração COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="d2af0-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="d2af0-103">Indica o resultado de uma busca de função armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="d2af0-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2af0-104">`COR_PRF_CACHED_FUNCTION_FOUND`tem um valor de zero, portanto `COR_PRF_JIT_CACHE` não pode ser usado como um substituto booliano.</span><span class="sxs-lookup"><span data-stu-id="d2af0-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2af0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2af0-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="d2af0-106">Membros</span><span class="sxs-lookup"><span data-stu-id="d2af0-106">Members</span></span>  
  
|<span data-ttu-id="d2af0-107">Membro</span><span class="sxs-lookup"><span data-stu-id="d2af0-107">Member</span></span>|<span data-ttu-id="d2af0-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2af0-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="d2af0-109">A pesquisa encontrou a função.</span><span class="sxs-lookup"><span data-stu-id="d2af0-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="d2af0-110">A pesquisa não encontrou a função.</span><span class="sxs-lookup"><span data-stu-id="d2af0-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2af0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2af0-111">Requirements</span></span>  
 <span data-ttu-id="d2af0-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2af0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2af0-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d2af0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2af0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2af0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2af0-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2af0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2af0-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2af0-116">See also</span></span>

- [<span data-ttu-id="d2af0-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="d2af0-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
