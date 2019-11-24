---
title: Interface ICorProfilerModuleEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 5c4efff46c2460ee77f5a8011dc80796ac62a69e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442701"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="21e6f-102">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="21e6f-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="21e6f-103">Fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos carregados pelo aplicativo ou pelo criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="21e6f-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21e6f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="21e6f-104">Methods</span></span>  
  
|<span data-ttu-id="21e6f-105">Método</span><span class="sxs-lookup"><span data-stu-id="21e6f-105">Method</span></span>|<span data-ttu-id="21e6f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="21e6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21e6f-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="21e6f-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="21e6f-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="21e6f-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="21e6f-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="21e6f-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="21e6f-110">Gets the number of managed modules that were loaded into the application.</span><span class="sxs-lookup"><span data-stu-id="21e6f-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="21e6f-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="21e6f-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="21e6f-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span><span class="sxs-lookup"><span data-stu-id="21e6f-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="21e6f-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="21e6f-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="21e6f-114">Moves the enumerator's cursor to the starting position of the sequence.</span><span class="sxs-lookup"><span data-stu-id="21e6f-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="21e6f-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="21e6f-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="21e6f-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span><span class="sxs-lookup"><span data-stu-id="21e6f-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21e6f-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="21e6f-117">Remarks</span></span>  
 <span data-ttu-id="21e6f-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span><span class="sxs-lookup"><span data-stu-id="21e6f-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="21e6f-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span><span class="sxs-lookup"><span data-stu-id="21e6f-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="21e6f-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span><span class="sxs-lookup"><span data-stu-id="21e6f-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e6f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21e6f-121">Requirements</span></span>  
 <span data-ttu-id="21e6f-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e6f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e6f-123">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21e6f-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21e6f-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21e6f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e6f-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e6f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e6f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21e6f-126">See also</span></span>

- [<span data-ttu-id="21e6f-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="21e6f-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="21e6f-128">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="21e6f-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="21e6f-129">Método EnumModules</span><span class="sxs-lookup"><span data-stu-id="21e6f-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
