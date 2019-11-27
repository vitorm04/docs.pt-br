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
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="4ef60-102">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="4ef60-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="4ef60-103">Fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos carregados pelo aplicativo ou pelo criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="4ef60-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ef60-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4ef60-104">Methods</span></span>  
  
|<span data-ttu-id="4ef60-105">Método</span><span class="sxs-lookup"><span data-stu-id="4ef60-105">Method</span></span>|<span data-ttu-id="4ef60-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ef60-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ef60-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="4ef60-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="4ef60-108">Obtém um ponteiro de interface para uma cópia desta `ICorProfilerModuleEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="4ef60-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="4ef60-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="4ef60-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="4ef60-110">Obtém o número de módulos gerenciados que foram carregados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ef60-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="4ef60-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="4ef60-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="4ef60-112">Obtém o número especificado de módulos contíguos de uma coleção sequencial de objetos, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="4ef60-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="4ef60-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="4ef60-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="4ef60-114">Move o cursor do enumerador para a posição inicial da sequência.</span><span class="sxs-lookup"><span data-stu-id="4ef60-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="4ef60-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="4ef60-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="4ef60-116">Avança a posição do cursor do enumerador para que o número especificado de elementos seja ignorado.</span><span class="sxs-lookup"><span data-stu-id="4ef60-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ef60-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ef60-117">Remarks</span></span>  
 <span data-ttu-id="4ef60-118">A interface `ICorProfilerModuleEnum` é um enumerador.</span><span class="sxs-lookup"><span data-stu-id="4ef60-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="4ef60-119">Ele permite que o destinatário de uma matriz Extraia elementos do remetente a uma taxa apropriada para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="4ef60-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="4ef60-120">Em outras palavras, o receptor é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando, assim, os problemas associados à passagem de matrizes grandes como parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="4ef60-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ef60-121">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4ef60-121">Requirements</span></span>  
 <span data-ttu-id="4ef60-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ef60-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ef60-123">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4ef60-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ef60-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ef60-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ef60-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ef60-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef60-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ef60-126">See also</span></span>

- [<span data-ttu-id="4ef60-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4ef60-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="4ef60-128">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="4ef60-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4ef60-129">Método EnumModules</span><span class="sxs-lookup"><span data-stu-id="4ef60-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
