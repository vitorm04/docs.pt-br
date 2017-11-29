---
title: "Método ICorProfilerCallback4::MovedReferences2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.MovedReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8137d944081475095509150cce84a611b7030eb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="fbf6c-102">Método ICorProfilerCallback4::MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="fbf6c-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="fbf6c-103">Chamado para o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação de relatório.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="fbf6c-104">Este método é chamado se o criador de perfil tiver implementado o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="fbf6c-105">Esse retorno de chamada substitui o [: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, porque ela pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expressa em um ULONG.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf6c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbf6c-106">Syntax</span></span>  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbf6c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbf6c-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="fbf6c-108">[in] O número de blocos de contíguos objetos que movidas como o resultado de compactação da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="fbf6c-109">Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total do `oldObjectIDRangeStart`, `newObjectIDRangeStart`, e `cObjectIDRangeLength` matrizes.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="fbf6c-110">Os próximos três argumentos de `MovedReferences2` matrizes paralelos.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="fbf6c-111">Em outras palavras, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, e `cObjectIDRangeLength[i]` todos diz respeito a um único bloco de objetos adjacentes.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="fbf6c-112">[in] Uma matriz de `ObjectID` valores, cada um deles é o antigo (coleta de lixo pré-lançamento) Iniciando endereço de um bloco de contígua, live objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="fbf6c-113">[in] Uma matriz de `ObjectID` valores, cada um deles é o novo endereço inicial (coleta de pós-lixo) de um bloco de contígua, live objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="fbf6c-114">[in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco de objetos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="fbf6c-115">Um tamanho é especificado para cada bloco que é referenciado no `oldObjectIDRangeStart` e `newObjectIDRangeStart` matrizes.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbf6c-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbf6c-116">Remarks</span></span>  
 <span data-ttu-id="fbf6c-117">Um coletor de lixo compactação recupera a memória ocupada por objetos inativos e compacta que liberado espaço.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="fbf6c-118">Como resultado, os objetos em tempo real podem ser movidos no heap, e `ObjectID` valores distribuídos por meio de notificações anteriores podem ser alterado.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="fbf6c-119">Suponha que um existente `ObjectID` valor (`oldObjectID`) está dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="fbf6c-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="fbf6c-120">Nesse caso, o deslocamento do início do intervalo para o início do objeto é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fbf6c-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="fbf6c-121">Para qualquer valor de `i` que está no seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="fbf6c-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="fbf6c-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="fbf6c-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="fbf6c-123">Você pode calcular o novo `ObjectID` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fbf6c-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="fbf6c-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="fbf6c-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="fbf6c-125">Nenhum do `ObjectID` valores passados pelo `MovedReferences2` são válidos durante o retorno de chamada em si, porque o coletor de lixo pode estar no meio de mover objetos de locais antigos para novos locais.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="fbf6c-126">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences2`.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="fbf6c-127">Um [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) retorno de chamada indica que todos os objetos foram movidos para seus novos locais e inspeção pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="fbf6c-128">Se o criador de perfil implementa ambos o [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `MovedReferences2` método é chamado antes do [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, mas somente se o `MovedReferences2` método retorna com êxito.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="fbf6c-129">Criadores de perfil podem retornar um HRESULT que indica uma falha do `MovedReferences2` método para evitar o segundo método de chamada.</span><span class="sxs-lookup"><span data-stu-id="fbf6c-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbf6c-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbf6c-130">Requirements</span></span>  
 <span data-ttu-id="fbf6c-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbf6c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbf6c-132">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fbf6c-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbf6c-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbf6c-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbf6c-134">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbf6c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf6c-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbf6c-135">See Also</span></span>  
 [<span data-ttu-id="fbf6c-136">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="fbf6c-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fbf6c-137">Método MovedReferences</span><span class="sxs-lookup"><span data-stu-id="fbf6c-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)  
 [<span data-ttu-id="fbf6c-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="fbf6c-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="fbf6c-139">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="fbf6c-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="fbf6c-140">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="fbf6c-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
