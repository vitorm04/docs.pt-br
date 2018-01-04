---
title: "Enumeração COR_PRF_GC_ROOT_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_ROOT_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords: COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e00f695edb94acbd54d6bd009ccd629aeec1b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="dc53a-102">Enumeração COR_PRF_GC_ROOT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="dc53a-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="dc53a-103">Indica uma propriedade de uma raiz de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="dc53a-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc53a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc53a-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="dc53a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dc53a-105">Members</span></span>  
  
|<span data-ttu-id="dc53a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dc53a-106">Member</span></span>|<span data-ttu-id="dc53a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc53a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="dc53a-108">A raiz impede uma coleta de lixo de mover o objeto.</span><span class="sxs-lookup"><span data-stu-id="dc53a-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="dc53a-109">A raiz não impede que a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="dc53a-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="dc53a-110">A raiz refere-se a um campo do objeto, em vez do próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="dc53a-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="dc53a-111">A raiz impede que a coleta de lixo se a contagem de referência do objeto é um determinado valor.</span><span class="sxs-lookup"><span data-stu-id="dc53a-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc53a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc53a-112">Remarks</span></span>  
 <span data-ttu-id="dc53a-113">`COR_PRF_GC_ROOT_FLAGS`é um bitmask que fornece informações adicionais sobre raízes especiais.</span><span class="sxs-lookup"><span data-stu-id="dc53a-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="dc53a-114">No entanto, nem todas as raízes são especiais.</span><span class="sxs-lookup"><span data-stu-id="dc53a-114">However, not all roots are special.</span></span> <span data-ttu-id="dc53a-115">Por exemplo, alguns raízes não são referências fracas, ponteiros internos, fixos ou contado por referência.</span><span class="sxs-lookup"><span data-stu-id="dc53a-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="dc53a-116">Para tal raízes, não há nenhum sinalizador para transmitir.</span><span class="sxs-lookup"><span data-stu-id="dc53a-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="dc53a-117">Portanto, os métodos que usam essa enumeração, como o [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) método send 0 para a máscara de bits de sinalizadores indicando que todos os sinalizadores são desativados.</span><span class="sxs-lookup"><span data-stu-id="dc53a-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc53a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc53a-118">Requirements</span></span>  
 <span data-ttu-id="dc53a-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc53a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc53a-120">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc53a-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc53a-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc53a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc53a-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc53a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc53a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc53a-123">See Also</span></span>  
 [<span data-ttu-id="dc53a-124">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="dc53a-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
