---
title: Método ICorProfilerCallback::MovedReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d13a291db484fd4e1d235ce3bb84a55118214379
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520406"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="a44ff-102">Método ICorProfilerCallback::MovedReferences</span><span class="sxs-lookup"><span data-stu-id="a44ff-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="a44ff-103">Chamado para relatar o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="a44ff-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a44ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a44ff-104">Syntax</span></span>  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a44ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a44ff-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="a44ff-106">[in] O número de blocos de objetos contíguos que movidas como resultado da compactação coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a44ff-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="a44ff-107">Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total do `oldObjectIDRangeStart`, `newObjectIDRangeStart`, e `cObjectIDRangeLength` matrizes.</span><span class="sxs-lookup"><span data-stu-id="a44ff-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="a44ff-108">Os próximos três argumentos de `MovedReferences` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="a44ff-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="a44ff-109">Em outras palavras, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, e `cObjectIDRangeLength[i]` todos dizem respeito a um único bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="a44ff-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="a44ff-110">[in] Uma matriz de `ObjectID` valores, cada um deles é o antigo (coleta de lixo de pré-lançamento) endereço de um bloco de contíguos inicial, os objetos dinâmicos na memória.</span><span class="sxs-lookup"><span data-stu-id="a44ff-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="a44ff-111">[in] Uma matriz de `ObjectID` valores, cada um deles é o novo endereço inicial (coleta de pós-lixo) de um bloco de contíguos, live objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="a44ff-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="a44ff-112">[in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco de objetos adjacentes na memória.</span><span class="sxs-lookup"><span data-stu-id="a44ff-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="a44ff-113">Um tamanho for especificado para cada bloco que é referenciado na `oldObjectIDRangeStart` e `newObjectIDRangeStart` matrizes.</span><span class="sxs-lookup"><span data-stu-id="a44ff-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a44ff-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="a44ff-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a44ff-115">Esse método informa os tamanhos como `MAX_ULONG` para objetos que são maiores que 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a44ff-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="a44ff-116">Para obter o tamanho dos objetos que são maiores que 4 GB, use o [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a44ff-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="a44ff-117">Um compactação coletor de lixo recupera a memória ocupada por objetos inativos e compacta que liberado espaço.</span><span class="sxs-lookup"><span data-stu-id="a44ff-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="a44ff-118">Como resultado, os objetos em tempo real podem ser movidos no heap, e `ObjectID` valores distribuídos por meio de notificações anteriores pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="a44ff-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="a44ff-119">Suponha que uma já existente `ObjectID` valor (`oldObjectID`) se encontra dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="a44ff-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="a44ff-120">Nesse caso, o deslocamento do início do intervalo para o início do objeto é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a44ff-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="a44ff-121">Para qualquer valor de `i` que está no seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="a44ff-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="a44ff-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="a44ff-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="a44ff-123">Você pode calcular o novo `ObjectID` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a44ff-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="a44ff-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="a44ff-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="a44ff-125">Nenhum dos `ObjectID` valores passados pelo `MovedReferences` são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de movimentação de objetos de locais antigos para novos locais.</span><span class="sxs-lookup"><span data-stu-id="a44ff-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="a44ff-126">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences`.</span><span class="sxs-lookup"><span data-stu-id="a44ff-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="a44ff-127">Um [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) retorno de chamada indica que todos os objetos foram movidos para os novos locais e inspeção pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="a44ff-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a44ff-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a44ff-128">Requirements</span></span>  
 <span data-ttu-id="a44ff-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a44ff-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a44ff-130">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a44ff-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a44ff-131">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a44ff-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a44ff-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a44ff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44ff-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a44ff-133">See also</span></span>
- [<span data-ttu-id="a44ff-134">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a44ff-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a44ff-135">Método MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="a44ff-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="a44ff-136">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a44ff-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a44ff-137">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a44ff-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
