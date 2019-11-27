---
title: Enumeração COR_PRF_GC_ROOT_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 174486a88192bd5ff11074930d5ad3375603f8a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449462"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="82fd1-102">Enumeração COR_PRF_GC_ROOT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="82fd1-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="82fd1-103">Indica uma propriedade de uma raiz de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="82fd1-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82fd1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82fd1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="82fd1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="82fd1-105">Members</span></span>  
  
|<span data-ttu-id="82fd1-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="82fd1-106">Member</span></span>|<span data-ttu-id="82fd1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="82fd1-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="82fd1-108">A raiz impede que uma coleta de lixo mova o objeto.</span><span class="sxs-lookup"><span data-stu-id="82fd1-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="82fd1-109">A raiz não impede a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="82fd1-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="82fd1-110">A raiz refere-se a um campo do objeto em vez do próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="82fd1-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="82fd1-111">A raiz impedirá a coleta de lixo se a contagem de referência do objeto for um determinado valor.</span><span class="sxs-lookup"><span data-stu-id="82fd1-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82fd1-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="82fd1-112">Remarks</span></span>  
 <span data-ttu-id="82fd1-113">`COR_PRF_GC_ROOT_FLAGS` é um bitmask que fornece informações adicionais sobre raízes especiais.</span><span class="sxs-lookup"><span data-stu-id="82fd1-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="82fd1-114">No entanto, nem todas as raízes são especiais.</span><span class="sxs-lookup"><span data-stu-id="82fd1-114">However, not all roots are special.</span></span> <span data-ttu-id="82fd1-115">Por exemplo, algumas raízes não são referências fracas, ponteiros interiores, fixados ou contados por referência.</span><span class="sxs-lookup"><span data-stu-id="82fd1-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="82fd1-116">Para essas raízes, não há nenhum sinalizador para transmitir.</span><span class="sxs-lookup"><span data-stu-id="82fd1-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="82fd1-117">Portanto, os métodos que usam essa enumeração, como o método [ICorProfilerCallback2:: RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) , enviam 0 para o bitmask dos sinalizadores, indicando que todos os sinalizadores estão desativados.</span><span class="sxs-lookup"><span data-stu-id="82fd1-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82fd1-118">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="82fd1-118">Requirements</span></span>  
 <span data-ttu-id="82fd1-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82fd1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82fd1-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="82fd1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82fd1-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82fd1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82fd1-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82fd1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82fd1-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82fd1-123">See also</span></span>

- [<span data-ttu-id="82fd1-124">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="82fd1-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
