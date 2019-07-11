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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f179e3b01d6c3b34dfa765565a0fc38d0ba867c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753691"
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="1d7eb-102">Enumeração COR_PRF_GC_ROOT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="1d7eb-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="1d7eb-103">Indica uma propriedade de uma raiz de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d7eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d7eb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="1d7eb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1d7eb-105">Members</span></span>  
  
|<span data-ttu-id="1d7eb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1d7eb-106">Member</span></span>|<span data-ttu-id="1d7eb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d7eb-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="1d7eb-108">A raiz impede que uma coleta de lixo mova o objeto.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="1d7eb-109">A raiz não impede a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="1d7eb-110">A raiz refere-se a um campo de objeto em vez do próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="1d7eb-111">A raiz impede a coleta de lixo se a contagem de referência do objeto é um valor determinado.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d7eb-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d7eb-112">Remarks</span></span>  
 <span data-ttu-id="1d7eb-113">`COR_PRF_GC_ROOT_FLAGS` é um bitmask que fornece informações adicionais sobre raízes especiais.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="1d7eb-114">No entanto, nem todas as raízes são especiais.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-114">However, not all roots are special.</span></span> <span data-ttu-id="1d7eb-115">Por exemplo, alguns raízes não são referências fracas, ponteiros interiores, fixos ou contado por referência.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="1d7eb-116">Para tais raízes, não há nenhum sinalizador para transmitir.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="1d7eb-117">Portanto, os métodos que usam essa enumeração, como o [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) método, envio de 0 para a máscara de bits de sinalizadores, indicando que todos os sinalizadores são desativados.</span><span class="sxs-lookup"><span data-stu-id="1d7eb-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d7eb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d7eb-118">Requirements</span></span>  
 <span data-ttu-id="1d7eb-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d7eb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d7eb-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d7eb-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d7eb-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d7eb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d7eb-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d7eb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d7eb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d7eb-123">See also</span></span>

- [<span data-ttu-id="1d7eb-124">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="1d7eb-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
